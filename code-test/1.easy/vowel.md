# 모음 자음 출력하기
## 개요
  입력된 문자열을 조건에 맞춰 출력하는 문제입니다.
  1. 모음을 먼저 출력합니다. 
  2. 자음을 출력합니다. 
  3. 문자열 출력시에는 순서가 변경되지 않고 유지되어야 합니다.
  4. 반복문을 사용하지 않는걸 권장합니다.
  5. 실제 출력 예제는 다음과 같습니다.

o  
i  
e  
c  
d  
n  
g  
t  
s  
t  

```javascript

function init() {
  const inputString = 'codingtest'
}

init()

```

## 출제의도
1. 반복문을 사용하지 않고 처리할 수 있는지 확인합니다.
2. 자바스크립트 ES6의 배열 함수에 대해 아는지 확인합니다.
3. ES6의 화살표 함수에 대해 아는지 확인합니다.

## 채점기준
1. 배열 함수형태로 호출해서 처리하는지 확인합니다.
2. 펑션을 생성하지 않고 화살표 함수로 만드는지 확인합니다.
3. 데이터를 나누고 처리하는 방법을 확인합니다.
4. 프로그램을 구동 했을때 답안이 출제 설명과 같은지 확인합니다.

## 답안 유형

```javascript
function init() {
  const inputString = 'codingtest'
  
  const arrayInputString = inputString.split('')
  
  const vowelList = ['a', 'e', 'i', 'o', 'u']
  
  const vowelArray = arrayInputString.filter(input =>
  	vowelList.find(vowel => vowel === input)
  )
  
  const otherArray = arrayInputString.filter(input => 
  	!vowelList.find(vowel => vowel === input)
  )
  
  const resultList = vowelArray.concat(otherArray)
  
  resultList.forEach(result => console.log(result))

}

init()
```
