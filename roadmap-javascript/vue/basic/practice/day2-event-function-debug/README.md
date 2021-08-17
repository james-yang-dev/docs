# 이벤트, 함수, 디버그

## 이론

### js 기본 이론
* https://www.w3schools.com/js/js_events.asp
* https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/함수
* https://www.w3schools.com/jsref/met_console_log.asp

### vue에서는
이벤트 앞에 'v-on'을 붙인다.

~~~html
<button v-on:click="doSomething">button</button>
~~~

함수는 'methods' 안에 정의합니다.

~~~js
methods: {
  doSomething: function () {
    // doSomething
  }
}
~~~

- [공홈 - 이벤트](https://kr.vuejs.org/v2/guide/events.html)


### 크롬 개발자 도구
option - command - i

console 탭 선택.

에러나 워닝을 그냥 넘어가지 말 것.


## 실습 과제
1. eslint 제거
    - 일단 지금 eslint가 뭔지는 패스하고 (코드 점검 툴) 공부 우선 순위를 위해서 제거합니다.
    - package.json 파일 안에 eslintConfig - extends 안에 "eslint:recommended" 라인 제거.
1. 만들어 놓은 프로젝트 내 기존 App.vue 파일에서 사용하지 않을 부분을 제거한다.
1. 버튼 한개를 추가한다. 버튼의 텍스트는 'add'로 한다.
1. 추가한 버튼에 click 이벤트를 건다.
1. 클릭 시 콘솔창에 'added!' 출력.

## 다음 고민
클릭할 때 마다 클릭 카운트 횟수를 콘솔창에 출력하려면?
