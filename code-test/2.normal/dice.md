# 주사위 굴리기
## 개요
  조건에 맞춰 주사위 굴리기의 결과값을 출력하는 함수입니다.
  1. 시작시 100~1000사이의 특정 숫자가 생성된다.
  2. 정육면체 주사위를 굴려 4 이상일때의 값을 누적한다.
  3. 누적 값의 총 합이 생성된 숫자의 값을 넘어서면 프로그램이 끝난다. 
  4. 끝나면서 다음과 같은 값을 콘솔로 출력한다.

## 제약사항
  - 소수점이 발생하면 2번째 자리 까지 반올림 출력한다.
  - 반복문은 사용할 수 없다. for, while 등
  - 전역변수 사용 금지.
  - 함수 안에 함수를 정의하지 말 것


```javascript

function getInputNumber() {
	return Math.floor(Math.random() * (1000 - 100)) + 100
}

function init() {
  const inputNumber = getInputNumber()
	// 
}

init()

```

## 출제의도
1. 반복문을 사용하지 않고 처리할 수 있는지 확인합니다.
2. 자바스크립트 ES6의 배열 함수에 대해 아는지 확인합니다.
3. ES6의 화살표 함수에 대해 아는지 확인합니다.
4. 재귀호출을 통해서 문제를 해결 할 수 있는지 확인합니다.

## 채점기준
1. 배열 함수형태로 호출해서 처리하는지 확인합니다.
2. 펑션을 생성하지 않고 화살표 함수로 만드는지 확인합니다.
3. 값을 누적하고 계산하는 방식을 확인합니다.
4. 프로그램을 구동 했을때 답안이 출제 설명과 같은지 확인합니다.

## 답안 유형
  총 횟수 : 178  
  4이상 횟수 : 83  
  3이하 횟수 : 95  
  생성값 : 420  
  누적값 : 421  
  누적 평균값 : 5.07  

```javascript

class diceObj {
  constructor() {
    this.fourUps = []
    this.inputNumber = 0
    this.cnt = 0
    this.sumNumber = 0
  }
}

function throwDice() {
  return Math.floor(Math.random() * 6 + 1)
}

function getInputNumber() {
  return Math.floor(Math.random() * (1000 - 100 + 1)) + 100
}

const rollDice = diceResult => {
  if (diceResult.sumNumber > diceResult.inputNumber) {
    return diceResult
  } else {
    const diceNumber = throwDice()
    if (diceNumber > 3) {
      diceResult.fourUps.push(diceNumber)
      diceResult.sumNumber += diceNumber
    }
    diceResult.cnt++
    rollDice(diceResult)
  }
}

function init() {
  // constr
  const diceResult = new diceObj()
  diceResult.inputNumber = getInputNumber()
  rollDice(diceResult)

  const sumNumber = diceResult.sumNumber
  const fourUps = diceResult.fourUps
  const sumAverage = (sumNumber / fourUps.length).toFixed(2)

  console.log(`총 횟수 : ${diceResult.cnt}`)
  console.log(`4이상 횟수 : ${fourUps.length}`)
  console.log(`3이하 횟수 : ${diceResult.cnt - fourUps.length}`)
  console.log(`생성값 : ${diceResult.inputNumber}`)
  console.log(`누적값 : ${sumNumber}`)
  console.log(`누적 평균값 : ${sumAverage}`)
}
init()


```
