# Vue

<table>
    <thead>
        <th>구분</th>
        <th>내용</th>
    </thead>
    <tbody>
        <tr>
            <td>요약</td>
            <td>front-end 라이브러리 Vue의 안내</td>
        </tr>
        <tr>
            <td>목표</td>
            <td>front-end 라이브러리 Vue 습득</td>
        </tr>
        <tr>
            <td>기대효과</td>
            <td>데이터 변경이 잦은 웹앱 개발시 효과적으로 개발을 진행</td>
        </tr>
    </tbody>
</table>

## 개념 이해
- Vue는 javascript 프레임워크 중 하나입니다.
- Vue는 데이터에 따라 DOM을 효율적으로 그려줍니다.

### 참조 문서
- [vue가 무엇인가요](https://kr.vuejs.org/v2/guide/#Vue-js가-무엇인가요)
- [프레임워크 간 비교](https://kr.vuejs.org/v2/guide/comparison.html)


## Vue 주요 요소

## Component
- 기본 html 엘리먼트를 확장하여 재사용 가능한 커스텀 엘리먼트
- 마크업, 자바스크립트 로직을 포함한 하나의 덩어리

### 참조 문서
- [컴포넌트가 무엇인가요](https://kr.vuejs.org/v2/guide/components.html#컴포넌트가-무엇인가요)


## Instance
- Vue 인스턴스란 생성된 Vue 오브젝트 하나
- Vue 앱을 시작하기 위해 필수적이며, 앱의 진입점이 됨


### 참조 문서
- [Vue 인스턴스](https://kr.vuejs.org/v2/guide/instance.html)


## Props
- props는 상위 컴포넌트의 정보를 하위 컴포넌트로 전달하기위한 사용자 지정 특성
![Props - Emit](https://kr.vuejs.org/images/props-events.png)


### 참조 문서
- [Props](https://kr.vuejs.org/v2/guide/components.html#Props)


## Lifecycle & Hook
- Vue 인스턴스 생명 주기
- 생명 주기 변화 과정에서 사용자 정의 로직을 실행할 수있는 라이프사이클 훅도 호출됩니다 ex) created/mounted
![라이프사이클 다이어그램](https://kr.vuejs.org/images/lifecycle.png)


### 참조 문서
- [인스턴스 라이프사이클 훅](https://kr.vuejs.org/v2/guide/instance.html#인스턴스-라이프사이클-훅)


## Directive
- 지시자
- Vue 엘리먼트에서 사용하는 특수한 속성
- v- 접두어가 붙어있으며 렌더링 된 DOM에 반응형 동작을 한다.
- v-if, v-for, v-on:click, v-bind:href, v-bind:src 등.. 이 있다.

### 참조 문서
- [디렉티브](https://kr.vuejs.org/v2/guide/syntax.html#디렉티브)



# Vue 주요 개념 실습

## 실습 전 준비
- Vue를 배우기 가장 간편한 환경인 vue-cli를 사용합니다.

### 참조 문서
- [vue-cli](https://cli.vuejs.org)
- [관련 실습 과제](https://github.kakaocorp.com/Techin/roadmap_javascript/tree/justin/vue/basic/practice/day1-prepare)


## 이벤트, methods, 디버그

### 참조 문서
- [vue event](https://kr.vuejs.org/v2/guide/events.html)
- [관련 실습 과제](https://github.kakaocorp.com/Techin/roadmap_javascript/tree/justin/vue/basic/practice/day2-event-function-debug)


## 데이터 바인딩

### 참조 문서
- [속성과 메서드](https://kr.vuejs.org/v2/guide/instance.html#속성과-메소드)
- [관련 실습 과제 - var](https://github.kakaocorp.com/Techin/roadmap_javascript/tree/justin/vue/basic/practice/day3-var)


## 리스트

### 참조 문서
- [리스트 렌더링](https://kr.vuejs.org/v2/guide/list.html)
- [관련 실습 과제 - array](https://github.kakaocorp.com/Techin/roadmap_javascript/tree/justin/vue/basic/practice/day4-array)
- [관련 실습 과제 - for](https://github.kakaocorp.com/Techin/roadmap_javascript/tree/justin/vue/basic/practice/day5-for)


## 디렉티브

### 참조 문서
- [디렉티브](https://kr.vuejs.org/v2/guide/syntax.html#디렉티브)
- [관련 실습 과제](https://github.kakaocorp.com/Techin/roadmap_javascript/tree/justin/vue/basic/practice/day6-directive)


