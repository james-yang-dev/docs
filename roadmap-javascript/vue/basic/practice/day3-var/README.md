# 변수

## 이론
- 변하는 수.
- 변수는 값 자체가 아닌, 값을 담는 그릇이라고 생각하면 된다.
  - ex) var justin = new Human();
- 전역변수
  - https://ko.wikipedia.org/wiki/전역_변수
- 지역변수
  - https://ko.wikipedia.org/wiki/지역_변수

### js 기본 이론
- https://developer.mozilla.org/ko/docs/Learn/JavaScript/First_steps/Variables
- https://www.w3schools.com/js/js_variables.asp

### vue에서는
컴포넌트 내에서 사용 가능한 변수는 'data'안에 아래와 같은 형태로 정의합니다. (일단 이렇게만 알고 넘어갑시다)
~~~js
data: function () {
  return {
    someVar: 'some value'
  }
}
~~~

템플릿 안에서 data에 정의 된 변수를 사용할 때는 이중 중괄호를 사용합니다.
~~~html
<h3>{{ someVar }}</h3>
~~~

다른 메서드 안에서 data에 정의 된 변수를 사용할 때는 앞에 this를 붙입니다.
(여기서 this는 변수가 정의 된 컴포넌트를 가르킴)
~~~js
methods: {
  doSomething: function () {
    console.log( this.someVar );
  }
}
~~~

### 여담
개발에 있어 네이밍은 정말 정말 중요하다.

변수명을 보면 이게 어떤 값인지 유추가 가능해야한다.
길어도 상관 없다. 의미가 우선이다.

ex) ft1팀 멤버의 수: var ft1TeamMemberCount = 14

개인 견해로는 값의 타입도 변수명에 포함하는 게 좋다고 본다.

ex) 'ft1팀 멤버의 수'는 숫자 타입이기 때문에
var nFt1TeamMemberCount = 14 (number 타입)

변수명만 봐도 위의 변수에 문자열을 넣어서는 안된다는 걸 알 수 있다.

## 실습 과제
1. 예제를 참고하여 기존 프로젝트의 버튼 클릭 이벤트 시 data에 정의 된 변수와 지역 변수를 사용하여 클릭 횟수를 콘솔창에 출력

## 다음 고민
data에 배열로 된 변수를 만들고 클릭할 때 마다 배열에 값을 추가할 것이다.
