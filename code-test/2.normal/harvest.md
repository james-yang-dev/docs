# 문자열 수확하기
## 개요
  조건에 맞춰 각기 다른 수확기가 돌때 결과값을 출력하는 함수입니다.
 1. 각각 운행주기가 다른 harvest1~3이 운행을 시작하고 field에서 문자열을 하나씩 수확한다.
 2. 필드의 문자열은 harvest의 구분없이 순차적으로 출력되어야 한다.
 3. 수확이 종료되면 마지막 harvest 수확 종료를 출력한다.

## 제약사항
  - 새로운 함수나 전역변수는 사용할 수 없다.

```javascript

// 필드 내용 구현
const fieldList = (function () {
	const innerField = ['m', 'i', 'w', 'w', 'u', 'j', 'y', 's', 'u', 'z', 'x', 'p', 'g', 'l', 'o', 'f']
})()


function getObject(harvest) {
  // 기능 구현
}

// 이하 수정 불가
let harvest1
let harvest2
let harvest3

function init() {
  harvest1 = setInterval(() => getObject('harvest1'), 700)
  harvest2 = setInterval(() => getObject('harvest2'), 1500)
  harvest3 = setInterval(() => getObject('harvest3'), 2200)
}

function stopHarvest() {
  clearInterval(harvest1)
  clearInterval(harvest2)
  clearInterval(harvest3)
}

init()


```

## 출제의도
1. 자바스크립트 인터벌에 대해 이해하는지 확인합니다.
2. 비동기로 처리되는 데이터에서 순차를 보장하는 방법을 확인합니다.
3. ES6의 화살표 함수에 대해 아는지 확인합니다.

## 채점기준
1. 제너레이터를 사용하는지 확인합니다.
2. async, await를 사용하는지 확인합니다.
3. 이벤트 다루는법을 확인합니다.
4. 프로그램을 구동 했을때 답안이 출제 설명과 같은지 확인합니다.

## 답안 유형
harvest1 : m  
harvest1 : i  
harvest2 : w  
harvest1 : w  
harvest3 : u  
harvest1 : j  
harvest2 : y  
harvest1 : s  
harvest1 : u  
harvest3 : z  
harvest2 : x  
harvest1 : p  
harvest1 : g  
harvest2 : l  
harvest1 : o  
harvest3 : f  
harvest1 : 수확 종료  

```javascript

const field = (function*() {
  const innerField = ['m', 'i', 'w', 'w', 'u', 'j', 'y', 's', 'u', 'z']
  for (const obj of innerField) yield obj
})()

function getObject(harvest) {
  const fieldObj = field.next()
  if (fieldObj.done) {
    stopHarvest()
    console.log('수확종료')
  } else {
    console.log(`${harvest} : ${fieldObj.value}`)
  }
}

let harvest1
let harvest2
let harvest3

function init() {
  harvest1 = setInterval(() => getObject('harvest1'), 700)
  harvest2 = setInterval(() => getObject('harvest2'), 1500)
  harvest3 = setInterval(() => getObject('harvest3'), 2200)
}

function stopHarvest() {
  clearInterval(harvest1)
  clearInterval(harvest2)
  clearInterval(harvest3)
}

init()


```
