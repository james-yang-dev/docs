# Javascript Beginner

<table>
    <thead>
        <th>구분</th>
        <th>내용</th>
    </thead>
    <tbody>
        <tr>
            <td>요약</td>
            <td>자바스크립트 초급자 가이드</td>
        </tr>
        <tr>
            <td>목표</td>
            <td>자바스크립트의 이해 및 기본기 쌓기</td>
        </tr>
        <tr>
            <td>예상시간</td>
            <td>20h</td>
        </tr>
        <tr>
            <td>기대효과</td>
            <td>자바스크립트 코드를 이해하고 참조하여 개발할 수 있다</td>
        </tr>
    </tbody>
</table>

## 목표
프로그래밍적 사고, 문제해결능력 기르기

## 대상자
프로그래밍 언어 입문자 혹은 JS를 다뤄봤으나 기본기부터 천천히 쌓고 싶은 분

## 진행 방식
주요실습 : 구구단 과제를 리펙토링 하면서 개념 익히기. [인프런 강의 섹션 4까지 ](https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1)
- 기초 스터디 전체에서 필요한 인프런 강의는 22,000원에 구입해야 합니다. 현재 개별 구매로 진행하고 있으나 경영지원부서에 회사에서 지원할 수 있도록 협의중입니다.

### 스터디 전 준비사항
- 이론 : 실습자, 리뷰어 모두 미리 개념을 훑어보고 실습자는 모르는 부분 체크하기 (제시된 자료 이외에 본인이 선택한 자료를 봐도 무방함. 같이 협의)
- 실습 : (실습자) 과제가 있는 경우 깃헙에 풀리퀘스트를 요청한다.
- 코드리뷰 : (리뷰어) 실습자가 요청한 풀리퀘스트를 보고 코드리뷰를 남긴다.

### 스터디
- 이론 : 같이 내용을 보면서 중요 개념 설명, 체크한 부분 질문 답변
- 코드리뷰 : 부연설명이 필요할 시 진행
- 다음주 과제 제시

## 예상소요시간
- 미리 준비하는 시간 제외한 스터디 2시간씩 2 * 10회 = 20시간

## 커리큘럼
### 1. 기초

- [프로그래밍이란?](https://poiemaweb.com/coding)
- [자바스크립트란?](https://poiemaweb.com/js-introduction)
  - 자바스크립트의 역사
  - AJAX의 등장
  - SPA
  - 자바스크립트 언어의 특징
  - ES5, 6
- [자바스크립트 개발 환경과 실행 방법](https://poiemaweb.com/js-hello-world)
- [브라우저 동작 원리](https://poiemaweb.com/js-browser)

### 2. 데이터타입과 변수

- [데이터타입과 변수](https://poiemaweb.com/js-data-type-variable) \(나중에 해도 되는 건 스킵\)
  - var의 문제점
  - 즉시실행함수
- [let, const설명](https://poiemaweb.com/es6-block-scope)
- [strict mode](https://poiemaweb.com/js-strict-mode)

### 3. 연산자

- [연산자](https://poiemaweb.com/js-operator)
- 과제 (필수 1개. 나머지는 선택)
  - 4-1. 두 수를 입력받아 4칙연산의 결과를 표시해 봅시다.
  - 4-2. BMI를 계산하는 프로그램을 작성해 봅시다.
  - 4-3. 화씨를 입력받아서 섭씨로 바꾸는 프로그램을 작성해 봅시다.
  - 4-4. 입력한 문자열의 길이를 알려주는 프로그램을 작성해 봅시다.

### 4. 조건문

- [인프런강의 - 조건문](https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/lecture/10688)

- 조건문 간단 설명 \(switch는 나중\)
- falsy값, !, !! 설명
- 과제 (필수 1개. 나머지는 선택)
  - 5-1. 입력받은 숫자가 홀수인지 짝수인지를 알려주는 프로그램을 작성해 봅시다.
  - 5-2. 입력받은 문자가 대문자로 되어 있으면 '대문자 문장입니다.' 소문자로 되어 있으면 '소문자 문장입니다.' 그 외에는 '보통 문장입니다.' 라고 출력하는 프로그램을 작성해 보세요.

### 5. 반복문

- [인프런강의 - 반복문1](https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/lecture/10689)
- [인프런강의 - 반복문2](https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/lecture/10702)

- while, for문
- break, continue
- 이중루프 (어려우면 다음과제)
- 과제 (필수 이외는 선택)
  - 6-1. (필수) 2단을 반복문으로 출력하기. 할 수 있으면 이중반복문으로 2~9단 구현도 해봅니다.
  - 6-2. 사용자가 입력한 수들의 갯수와 합을 구하는 프로그램을 작성해 봅시다. (단 0을 입력받으면 입력 종료)
  - 6-3. 1에서 100까지 짝수의 합을 구해 봅시다.
  - 6-4. 100, 99, 98, ..., 0 까지 출력하는 프로그램을 작성해 봅시다.  

### 6. 배열

- [인프런강의 - 배열](https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/lecture/10703)
- [과제 - 배열로 구구단 리펙토링](https://front-end-team.gitbook.io/front-end/freeform-project/array1)

### 7. 함수

- [인프런강의 - 배열로 구구단 리펙토링 강의](https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/lecture/10712)
- [인프런강의 - 함수. 함수의 정의와 호출](https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/lecture/10704)
- [인프런강의 - 함수. 함수와 리턴값](https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/lecture/10705)
- [과제 - 함수로 구구단 리펙토링](https://front-end-team.gitbook.io/front-end/freeform-project/function)

### 8. 객체

- [인프런강의 - 함수로 구구단 리펙토링 강의](https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/lecture/10714)
- [인프런강의 - 객체](https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/lecture/10706)
- 속성과 메소드
- 객체에서 this
- [과제 - 객체로 구구단 리펙토링](https://front-end-team.gitbook.io/front-end/freeform-project/object)

### 9. DOM, this

- [자바스크립트의 this - 코드종](https://www.youtube.com/watch?v=PAr92molMHU&list=PLuBMRNcyzsWxcnDdAmJWyWYXuExyP9aS1&index=6)
- [DOM, 유사배열객체](https://poiemaweb.com/js-dom)
- [과제 - Select 박스](https://front-end-team.gitbook.io/front-end/freeform-project/select)

## freeform project (자유과제: 본인이 하고 싶은 과제 진행 후 코드리뷰)

- [inputNumber](https://front-end-team.gitbook.io/front-end/freeform-project/inputnumber)
- [Modal \(layer popup\)](https://front-end-team.gitbook.io/front-end/freeform-project/modal-layer-popup)
- [BMI](https://front-end-team.gitbook.io/front-end/freeform-project/bmi)
- [PrimeNumber](https://front-end-team.gitbook.io/front-end/freeform-project/primenumber)
- [배열에서 최대값, 최소값, 평균값, 홀수값 구하기](https://front-end-team.gitbook.io/front-end/freeform-project/array)
- [간단한 이미지 슬라이드](https://front-end-team.gitbook.io/front-end/freeform-project/function2)

## 스터디 종료 후(권장)
- 개발 언어를 익힌다는건 말을 배우는 것과 같아서 반복 실습을 해 주어야 합니다. 이론적으로 배운 내용들을 아래 강의들을 통해 자연스럽게 습득할 수 있을 것 이라 생각합니다.
- [자바스크립트 게임 만들기](https://www.inflearn.com/course/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EA%B2%8C%EC%9E%84-%EA%B0%9C%EB%B0%9C)
