# 반목문 for

## 이론

### js 기본 이론
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Loops_and_iteration
- https://www.w3schools.com/js/js_loop_for.asp

### vue에서는
- 반복문을 이용해서 그릴 때는 'v-for'를 사용한다.
- 문법은 'item in 배열' 형태, 또는 '(item, index) in 배열' 형태를 사용한다.
문법은 암기하세요...
- 여기서 'item'은 배열 안의 각 값, 'index'는 배열 안의 각 아이템의 순번이 들어온다.

~~~html
<ul>
  <li v-for="item in arrItems">
    {{ item.message }}
  </li>
</ul>
~~~

~~~js
data: {
  arrItems: [
    { message: 'Foo' },
    { message: 'Bar' }
  ]
}
~~~

- [vue - list](https://kr.vuejs.org/v2/guide/list.html)

## 실습 과제
1. 진행 중인 프로젝트에 v-for 적용 (샘플 파일 참고)
  - v-bind:key="index" 이 부분은 다음에 배울 것이기 때문에 넘어간다.

## 다음 고민
v-bind가 무엇인가.