# vue 디렉티브

## 이론

- 디렉티브는 Vue에서 제공하는 특수 속성.
- v- 접두어가 붙어있으며 렌더링 된 DOM에 반응형 동작을 한다.
- ex) v-if, v-for, v-on:click, v-bind:href, v-bind:src 등..

- https://kr.vuejs.org/v2/guide/index.html 에서 '디렉티브' 검색.
- https://kr.vuejs.org/v2/guide/syntax.html 에서 '디렉티브' 검색.

- 각 디렉티브마다 고유한 기능이 있다.

- 디렉티브 중 v-bind는 반응적으로 HTML 속성을 갱신하는데 사용됩니다.
  ~~~html
  <img src="http://google.com">
  <!-- 단순 문자열 -->
  ~~~

  ~~~js
  data() {
    return {
      url = "http://google.com";
    }
  }
  ~~~
  ~~~html
  <img v-bind:src="url">
  <!-- 변수 url을 연결 -->
  ~~~

### 약어 제공

- 가장 자주 사용 되는 두개의 디렉티브인 v-bind, v-on에 대해 약어를 제공한다.
- https://kr.vuejs.org/v2/guide/syntax.html 에서 '약어' 검색.
- ex) v-bind:src -> :src
- ex) v-on:click -> @click


## 실습 과제
1. 실습 프로젝트 안 약어로 변경 가능한 모든 디렉티브를 약어로 바꾼다.

1. 진행 중인 프로젝트의 li 태그 안에 그냥 이미지 주소로 된 문자열을 넣었었는데, img 태그를 이용하여 해당 이미지 주소로 이미지를 그린다. (이미 진행 완료 했다면 해당 없음)


## 다음 고민 (과제?)
1. 현재 click 이벤트가 걸려 있는 버튼이 한 개가 있는데, 네 개 더 추가해 다섯 개를 만든다.
1. 추가한 버튼 클릭 시에도 이미지를 추가하는데, 다섯 개 버튼 다 다른 경로를 추가한다.