# Javascript Intermediate

<table>
    <thead>
        <th>구분</th>
        <th>내용</th>
    </thead>
    <tbody>
        <tr>
            <td>요약</td>
            <td>자바스크립트 중급자 가이드</td>
        </tr>
        <tr>
            <td>목표</td>
            <td>자바스크립트의 역량 및 실무 능력 향상</td>
        </tr>
        <tr>
            <td>기대효과</td>
            <td>업무 효율 향상 및 웹 페이지 성능 개선</td>
        </tr>
    </tbody>
</table>

# 목차
- [ES6](#ES6)
- [배열](#배열)
- [객체, 함수](#객체,-함수)
- [비동기식과 콜백](#비동기식과-콜백)
- [비동기식에 대한 새로운 처리](#비동기식에-대한-새로운-처리)
- [실행 콘텍스트와 유효범위](#실행-콘텍스트와-유효범위)
- [일급객체와 고차함수](#일급객체와-고차함수)
- [재귀](#재귀)

## ES6
자바스크립트는 ES6를 기준으로 새롭게 바뀌었습니다. 새로운 개념 및 문법이 대거 등장하였습니다.
중급과정에서 필수로 사용해야 하는 ES6와 관련된 주요 변경사항들에 대해 익혀봅니다.

### 참고 자료
- [let, const와 블록 레벨 스코프](https://poiemaweb.com/es6-block-scope)
- [템플릿 리터럴](https://poiemaweb.com/es6-template-literals)
- [화살표 함수](https://poiemaweb.com/es6-arrow-function)

## 배열
배열에는 많은 함수가 존재하며, 배열을 능숙하게 다루는것이 실무를 빠르고 효율적으로 처리할 수 있는 지름길 입니다.
아래 자료를 통해 배열에 대한 이해도를 더욱 높일 수 있습니다.

### 참고 자료
- [Array 객체](https://poiemaweb.com/js-array)
- [Array 객체 - MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)

## 객체 그리고 함수
객체, 그리고 함수와 관련되어 ES6에서 등장한 새로운 개념들을 아래 자료를 통해 익힙니다.
강력해진 객체는 자바스크립트를 조금 더 함수지향적으로 개발할 수 있도록 도와줍니다.

### 참고 자료
- [매개변수 기본값, Rest 파라미터, Spread 문법, Rest/Spread 프로퍼티](https://poiemaweb.com/es6-extended-parameter-handling)
- [객체 리터럴 프로퍼티 기능 확장](https://poiemaweb.com/es6-enhanced-object-property)
- [클래스](https://poiemaweb.com/es6-class)
- [모듈](https://poiemaweb.com/es6-module)
- [디스트럭처링](https://poiemaweb.com/es6-destructuring)
- [7번째 타입 심볼(Symbol)](https://poiemaweb.com/es6-symbol)

## 비동기식과 콜백
비동기식 방식은 최근 웹에서 항상 다뤄지는 아주 중요한 개념 중 하나입니다.
비동기식을 처리하며 필연적으로 처리해야 하는 콜백에 대한 개념까지 자료를 통해 숙지합니다.

### 참고 자료
- [비동기식 처리 모델과 Ajax](https://poiemaweb.com/js-ajax)
- [값으로서의 함수와 콜백 - 생활코딩](https://www.opentutorials.org/course/743/6508)
- [콜백함수의 동기와 비동기 - 코드종](https://www.youtube.com/watch?v=j0Viy3v97gY&list=PLuBMRNcyzsWxcnDdAmJWyWYXuExyP9aS1&index=3)

## 비동기식에 대한 새로운 처리
콜백의 불편함은 새로운 비동기식 처리를 만드는 마중물이 되었습니다.
프로미스부터 가장 강편하고 강력한 async/await 까지 익히며 오류를 최소화하고 공통으로 처리하여 어플리케이션에 대한 안정성을 향상시킵니다. 

### 참고 자료
- [프로미스](https://poiemaweb.com/es6-promise)
- [이터레이션과 for...of 문](https://poiemaweb.com/es6-iteration-for-of)
- [제너레이터와 async/await](https://poiemaweb.com/es6-generator)

## 실행 콘텍스트와 유효범위

자바스크립트는 V8 앤진위에서 돌아가는 인터프리팅 형식을 가진 언어입니다.  
메모리를 힙에 저장하고, 콜스택이라는 실행환경을 가지게 됩니다.  
유효범위, 이를 응용한 클로저, 호이스팅 실행콘텍스트 등 자바스크립트의 동작원리에 대해 배웁니다.

### 참고 자료
- [Scope](http://www.nextree.co.kr/p7363/)
- [Closure](https://hyunseob.github.io/2016/08/30/javascript-closure/)
- [Hoisting](https://gmlwjd9405.github.io/2019/04/22/javascript-hoisting.html)
- [Excuting Context](https://joshua1988.github.io/web-development/translation/javascript/how-js-works-inside-engine/)

## 일급객체와 고차함수

자바스크립트의 함수는 일급개체입니다. 함수의 인자로 함수 자체를 전달 할 수 있습니다.  
이것을 응용하여 함수를 인자로 받고 함수를 리턴하는 형식의 커링(Currying) 이라는 기법을 사용할 수 있습니다.  
배열의 고차함수의 활용법 및 원리와 기법을 배웁니다.

### 참고 자료
- [High Order Function](https://poiemaweb.com/js-array-higher-order-function)
- [Currying](https://www.zerocho.com/category/JavaScript/post/579236d08241b6f43951af18)

## 재귀

재귀를 간단하게 정의하면 한 함수가 자기 자신을 호출하는 순간입니다.
재귀함수를 연습하다 보면 여러번 컴퓨터가 무한루핑에 빠져 비행기 이륙소리를 내던것을 떠올리게 됩니다.
재귀함수는 3가지 중요한 특성이 있습니다.

```text
1. 종료조건
2. 기반조건
3. 재귀
```

재귀함수는 너무 많이 호출되면 스택을 터트리는 주범이기도 합니다.
재귀함수의 활용 및 주의사항에 대해 배웁니다.

### 참고 자료

- [Recursion](https://velog.io/@jakeseo_me/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%9D%BC%EB%A9%B4-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%A0-33%EA%B0%80%EC%A7%80-%EA%B0%9C%EB%85%90-23-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%AC%EA%B7%80Recursion-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0)

## 자바스크립트 실습
- [자바스크립트 기본기](https://www.youtube.com/watch?v=wUHncG3VwPw&list=PL7jH19IHhOLM8YwJMTa3UkXZN-LldYnyK)

## 자바스크립트를 더 많이 알아보기(권장)

좋은 자바스크립트 개발자가 되기 위해 알아야 할 내용들이 더 있습니다.  
몰라도 개발은 할 수 있지만, 잘 하기 위해서는 알아야 할 내용들이라고 생각합니다.

- [33가지 자바스크립트 컨셉](https://github.com/leonardomso/33-js-concepts)
- [33가지 자바스크립트 컨셉-한글화](https://github.com/Lee-hyuna/33-js-concepts-kr/wiki)
- [현대 자바스크립트 자습서](https://javascript.info/)
- [다양한 자바스크립트 설계 패턴](https://www.dofactory.com/javascript/design-patterns)
