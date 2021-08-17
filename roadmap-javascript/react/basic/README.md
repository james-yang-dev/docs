# React

<table>
    <thead>
        <th>구분</th>
        <th>내용</th>
    </thead>
    <tbody>
        <tr>
            <td>요약</td>
            <td>front-end 라이브러리 React의 안내</td>
        </tr>
        <tr>
            <td>목표</td>
            <td>front-end 라이브러리 React 습득</td>
        </tr>
        <tr>
            <td>기대효과</td>
            <td>데이터 변경이 잦은 웹앱 개발시 효과적으로 개발을 진행</td>
        </tr>
    </tbody>
</table>




# 개념 이해

리액트는 어떤 데이터가 변할 때마다 DOM의 어떤 변화를 줄지 고민을 덜하도록 만든 라이브러리 입니다. 
리액트는 개발자가 그저 뷰가 어떻게 생길지 선언하고 데이터에 변화가 있으면 정해진 규칙에 따라 성능을 아끼면서 렌더링을 할 수 있도록 만듭니다.

여기서 렌더링은 사용자 화면에 뷰를 보여주는 것을 말합니다. 


# React의 렌더링



## 초기 렌더링

- render() 함수를 통해서 컴포넌트가 어떻게 생겼는지 정의를 합니다.
- render() 함수는 html 형식의 문자열을 반환하지 않고, 뷰가 어떻게 생겼고 어떻게 작동하는지에 대한 정보를 지닌 객체를 반환합니다. 
- 컴포넌트 내부에는 또 다른 컴포넌트들이 들어갈 수 있습니다.
- 최상위 컴포넌트의 렌더링 작업이 끝나면 지니고 있는 정보들을 사용하여 HTML 마크업을 만들고, 이를 우리가 정하는 실제 페이지의 DOM 요소 안에 주입합니다.
- 먼저 문자열 형태의 HTML 코드를 생성한 후 특정 DOM에 해당 내용을 주입하면 이벤트가 적용됩니다.



## 업데이트 렌더링

- 컴포넌트에서 데이터에 변화가 있을때 뷰가 변형되는 것처럼 보이지만, 사실은 새로운 요소로 갈아 끼웁니다.
- 이 작업 또한 render() 함수가 작업을 진행합니다. 컴포넌트는 데이터를 업데이트 했을 때 단순히 업데이트한 값을 수정하는 것이 아니라, 새로운 데이터를 가지고 render 함수를 또 다시 호출합니다.
- 이때 render 함수가 반환하는 결과를 곧바로 DOM에 반영하지 않고, 이전에 render 함수가 만들었던 컴포넌트 정보와 현재 render 함수가 만든 컴포넌트 정보를 비교 합니다.
- 둘의 차이를 알아내 최소한의 연산으로 DOM 트리를 업데이트 합니다.

# React 주요 요소



## Element
- Element는 DOM 노드 또는 다른 컴포넌트와 관련하여 화면에 표시할 내용을 설명하는 일반 개체입니다. 

```javascript
// element의 형태
{
  type: 'button',
  props: {
    className: 'button button-blue',
    children: {
      type: 'b',
      children: 'OK!'
    }
  }
}
```

### 참조 문서
- [Rendering Elements](https://ko.reactjs.org/docs/rendering-elements.html)
- [Dan Abramov의 React Component, Elements and Instances](https://medium.com/@dan_abramov/react-components-elements-and-instances-90800811f8ca)




## Component


- component는 2가지 형태 (class , function) 으로 존재 할 수 있습니다.
- class component 는 React.Component를 상속받아 render 메서드를 지닌 형태이고 일반 함수 형태로도 표현할 수 있습니다.
- class component , function component 이 둘다 입력으로 props를 받고 산출물로 element tree를 반환합니다.

### 참조 문서
- [Componentns and Props](https://ko.reactjs.org/docs/components-and-props.html)
- [Dan Abramov의 React Component, Elements and Instances](https://medium.com/@dan_abramov/react-components-elements-and-instances-90800811f8ca)



## Instance
- class component 에서 사용되는 this로 참조되는 값입니다.
- instance는 local state를 저장하고 lifecycle event에 반응하기에 적합합니다.


### 참조 문서
- [Dan Abramov의 React Component, Elements and Instances](https://medium.com/@dan_abramov/react-components-elements-and-instances-90800811f8ca)


# React 주요 개념

## Virtual DOM
- DOM은 객체로 문서 구조를 표현하는 방법으로 XML이나 HTML로 작성합니다.
- 웹 브라우저는 DOM을 활용하여 객체에 자바스크립트와 CSS를 적용합니다. DOM은 트리 형태라서 특정 노드를 찾거나 수정하거나 제거하거나 원하는 곳에 삽입할 수 있습니다.
- DOM 자체는 빠릅니다. DOM 자체를 읽고 쓸 때의 성능은 자바스크립트 객체를 처리할 때의 성능과 비교하여 다르지 않습니다.
- 단, 웹 브라우저 단에서 DOM에 변화가 일어나면 웹 브라우저가 CSS를 다시 연산하고, 레이아웃을 구성하고, 페이지를 리페인트 합니다. 이 과정에서 시간이 허비 되는 것입니다.그렇기 떄문에 DOM을 최소한으로 조작하여 작업을 처리하는 방식으로 개선할 수 있습니다. 
- 리액트는 Virtaul DOM 방식을 사용하여 DOM 업데이트를 추상화함으로써 DOM 처리 횟수를 최소화하고 효율적으로 진행합니다. 

### 참조 문서
- [React 작동 방법](https://d2.naver.com/helloworld/9297403)
- [왜 Virtual DOM 인가?](https://velopert.com/3236)

### 실습
- [virtual-dom example](https://github.com/Matt-Esch/virtual-dom)



## Reconcliation
- 리액트에서 데이터가 변하여 웹 브라우저에 실제 DOM을 업데이트할 때는 다음 세 가지 절차를 밟습니다.
  - 데이터를 업데이트 하면 전체 UI를 Virtual DOM에 리렌더링 합니다.
  - 이전 VIrtaul DOM에 있던 내용과 현재 내용을 비교 합니다.
  - 바뀐 부분만 실제 DOM에 적용합니다.
- Virtaul DOM을 사용한다고 해서 사용하지 않을 때와 비교하여 무조건 빠른 것은 아닙니다. 
- 리액트는 "지속적으로 데이터가 변화하는 대규모 애플리케이션" 에 진가를 비로소 발휘 할 수 있습니다. 
- 리액트와 Virtal DOM이 언제나 제공할 수 있는 것은 바로 업데이트 처리 간결성입니다.  UI를 업데이트 하는 과정에서 생기는 복잡함을 모두 해소하고, 더욱 쉽게 업데이트에 접근할 수 있습니다.

### 참조 문서
- [Reconciliation](https://ko.reactjs.org/docs/reconciliation.html)
- [React 렌더링과 성능 알아보기](https://meetup.toast.com/posts/110)
- [React의 렌더링 알고리즘](https://www.huskyhoochu.com/virtual-dom/)


## Props 
- 컴포넌트 속성을 설정할 때 사용하는 요소입니다.
- `props` 값은 해당 컴포넌트를 불러와 사용하는 부모 컴포넌트에서 설정할 수 있습니다.
- `props` 값을 따로 지정하지 않았을 때 보여줄 기본값을 설정하는 `defaultProps` 가 있습니다.
- `props`는 컴포넌트가 사용되는 과정에서 부모 컴포넌트가 설정하는 값이며, 컴포넌트 자신은 해당 `props`를 읽기 전용으로만 사용할 수 있습니다. `props`를 바꾸려면 부모 컴포넌트에서 바꾸어 주어야 합니다. 
- 태그 사이의 내용을 보여주는 `children` 속성도 있습니다.
- `propTypes`를 통한 props 검증도 가능합니다.

```javascript
import React from 'react'
import PropTypes from 'prop-types'
 
 
// 화살표 문법
const MyComponent = props => {
    return <div>나의 새롭고 멋진 {props.name} 컴포넌트</div>
}
 
 
MyComponent.defaultProps = {
    name: '기본 이름'
}
MyComponent.propTypes = {
    name PropTypes.string
}
 
 
export default MyComponent
```

### 참조 문서
- [Components and Props](https://ko.reactjs.org/docs/components-and-props.html)


## JSX
- React는 component와 동작하고 모든 것은 component 입니다.
- 우리의 목적은 component를 보기 좋게 만드는 것입니다.
- component가 data를 보여주게 하는 것입니다.
- component는 HTML을 반환하는 함수 입니다.
- react는 component를 사용해서 HTML처럼 작성하려는 경우에 필요 합니다.
- javascript와 HTML 사이의 이러한 조합을 JSX라고 부릅니다.
- component를 만들고 사용하는데 있어서 React에서 만든 JSX 라는 것을 사용하게 됩니다.
- jsx는 babel을 통해서 createElement 함수로 바뀌고 실행됩니다.

### 참조 문서
- [JSX 소개](https://ko.reactjs.org/docs/introducing-jsx.html)


## Composition
- 컴포넌트에서 다른 컴포넌트를 `children` 이나 `props` 로 받아서 구성할 수 있다.
- 일반적인 컴포넌트에서 특수한 경우인 경우를 고려해야하는 경우 더 "구체적인" 컴포넌트가 "일반적인" 컴포넌트를 렌더링하고 구체적인 내용은 `props` 를 통해 내용을 구성한다.
- 가끔은 상위 컴포넌트에서 하위 컴포넌트에 필요한 데이터를 `props` 로 해당 하위컴포넌트에 전달할때 depth가 너무 깊으면 힘들어지니 상위 컴포넌트에서 데이터를 포함한 해당 하위 컴포넌트를 품고 `props` 로 전달해서 render 하면 더 편할 때가 있다. 다 편한건 아니다.

### 참조 문서
- [composition vs inheritance](https://ko.reactjs.org/docs/composition-vs-inheritance.html)


## Ref
- 리액트 프로젝트 내부에서 DOM에 이름을 다는 방법을 `ref(reference의 줄임말)` 이라고 합니다. 
- `ref는` 'DOM을 꼭 직접적으로 건드려야 할 때' 사용 해야 합니다. 
  - 특정 input에 포커스 주기
  - 스크롤 박스 조작하기
  - Canvas 요소에 그림 그리기

### 참조 문서
- [Ref와 DOM](https://ko.reactjs.org/docs/refs-and-the-dom.html)


## Life Cycle
- life cycle method는 react가 component를 생성하는 그리고 없애는데 호출되는 메서드 이다.
- component가 생성될 때, render 전에 호출되는 몇가지 function 이 있다.
- mount, update, unmount 때에 따라 호출되는 method가 있다.
- mount
    - `contstructor()` : 컴포넌트를 새로 만들 때마다 호출되는 클래스 생성자 메서드 입니다.
    - `static getDerivedStateFromProps()` : 컴포넌트가 인스턴스화 된 후, 새 props를 받았을 때 호출된다. props에 있는 값을 state에 넣을 때 사용하는 메서드 입니다.
    - `render()` : 우리가 준비한 UI를 렌더링하는 메서드 입니다. 
    - `componentDidMount()` : 컴포넌트가 웹 브라우저상에 나타난 후 호출하는 메서드입니다.
- update
    - `static getDerivedStateFromProps()` : 이 메서드는 마운트 과정에서도 호출되며, 업데이트가 시작하기 전에도 호출됩니다. props의 변화에 따라 state 값에도 변화를 주고 싶을 때 사용합니다.
    - `shouldComponentUpdate()` : 컴포넌트가 리렌더링을 해야 할지 말아야 할지를 결정하는 메서드 입니다. 이 메서드에서는 true 혹은 false 값을 반환하며, true을 반환하면 다음 라이프사이클 메서드를 계속 실행하고, false를 반환하면 작업을 중지합니다. 즉, 컴포넌트가 리렌더링 되지 않습니다. 만약 특정 함수에서 this.forceUpdate() 함수를 호출하면 이 과정을 생략하고 바로 render 함수를 호출합니다.
    - `render()` : 컴포넌트를 리렌더링 합니다.
    - `getSnapshotBeforeUpdate()` : DOM이 업데이트 직전에 호출된다. (이 라이프 사이클은 많이 필요하지 않지만, 렌더링되는 동안 수동으로 스크롤 위치를 유지해야할 때와 같은 경우에는 유용할 수 있다)
    - `componentDidUpdate()` : 컴포넌트의 업데이트 작업이 끝난 후 호출하는 메서드 입니다.
- unmount
    - `componentWillUnmount()` : 컴포넌트가 웹 브라우저상에서 사라지기 전에 호출하는 메서드 입니다.


### 참조 문서
- [State와 생명주기](https://ko.reactjs.org/docs/state-and-lifecycle.html)


## Immutability (변경불가성)


- Immutability(변경불가성)는 객체가 생성된 이후 그 상태를 변경할 수 없는 디자인 패턴 입니다.
- Javascript의 원시 타입(primitive data type)은 변경 불가능한 값(immutable value) 입니다.
- 원시 타입 이외의 모든 값은 객체(Object) 타입이며 객체 타입은 변경 가능한 값(mutable value) 입니다. 즉, 객체는 새로운 값을 다시 만들 필요없이 직접 변경이 가능하다는 것입니다.
- React에서 Immutability은 성능과 관련되서 중요한 담당을 합니다.
- React에서는 state가 변경이 되어서 재 렌더링이 필요한 경우에는 객체나 함수를 immutable하게 처리를 해주어야 합니다. 즉, 새로운 객체나 함수를 적용해야 한다는 뜻입니다. 하지만, 값이 변하지 않았는데 매번 새로운 immutable 한 값이 생성이 된다면 새로운 값으로 간주하여 불필요한 렌더링이 발생이 되어 주의를 요합니다.

```javascript
import React from 'react'

// App이 렌더링이 될떄 아래와 같이 Button 컴포넌트에 인라인 함수를 props로 넣게 되면 매 렌더링 시 마다 새로운 함수로 간주하여 
// 불필요한 Button도 렌더링이 발생하게 됩니다.
const App = () => {
  return (
    <div>
      <List></List>
      <Button onClick={() => console.log('click')}></Button>
    </div>
  )
}

// 함수형 컴포넌트에서는 아래처럼 컴포넌트 밖으로 빼두는게 좋습니다.

const handleClick = () => console.log('click')

const App = () => {
  return (
    <div>
      <List></List>
      <Button onClick={handleClick}></Button>
    </div>
  )
}

// 함수형 밖으로 빼는게 여의치 않으면 class 컴포넌트로 메서드를 등록해서 사용할 수 있습니다.
class App extends React.Component {

  handleClick() {
    console.log('click')
  }

  render() {
    return (
      <div>
        <List></List>
        <Button onClick={this.handleClick}></Button>
      </div>
    )
  }
}
```

### 참조 문서

- [객체와 변경불가성](https://poiemaweb.com/js-immutability)

## Fiber
- `reconciliation` 로직은 재귀를 통해서 `Element tree` 구조의 변화를 감지하고 최종적으로 DOM을 그려낸다. 이 비용이 높아지면 브라우저의 메인 쓰레드를 잡아 먹기 때문에 동시에 다른 비싼 비용들의 로직들을 처리 해 낼수가 없다. ( 버벅이는 현상이 나타남 )
- 기존의 재귀 용법에서 `iterator`, 즉 반복문 형태로 구조를 바꾸고 (tree구조를 선형적으로 바꾸게 됨) react 스케쥴링을 통해서 cpu가 idle인 경우일 때 일부 `reconcile을` 처리하고 이 반복이 모두 완료가 되었을 때, 최종적으로 DOM에 그리게 되는 형식이다. DOM 을 그릴 때는 동기적으로 한번에 그리게 됩니다.

### 참조 문서
- [how and why Fiber](https://medium.com/react-in-depth/the-how-and-why-on-reacts-usage-of-linked-list-in-fiber-67f1014d0eb7)
- [Inside Fiber 1 - new reconciliation algorithm](https://medium.com/react-in-depth/inside-fiber-in-depth-overview-of-the-new-reconciliation-algorithm-in-react-e1c04700ef6e)
- [Inside Fiber 2 - state and props update in React](https://medium.com/react-in-depth/in-depth-explanation-of-state-and-props-update-in-react-51ab94563311)


# 컴포넌트 상태관리

## State (Class Component)
- 리액트에서 `state`는 컴포넌트 내부에서 바뀔 수 있는 값을 의미합니다. 
- 리액트에는 두 가지 종류의 `state`가 있습니다. 하나는 클래스형 컴포넌트가 지니고 있는 `state`이고, 다른 하나는 함수형 컴포넌트에서 `useState`라는 함수를 통해 사용하는 `state` 입니다. 


### setState 

- `setState`로 `state`를 변경하고 새로 Render가 필요할때 사용합니다.
- `state`를 변경하고자 할때 직접적으로 변경하는 것이 아니라 `setState` 메서드를 사용해서 변경합니다.
- `setState`를 호출하게 되면 React의 스케쥴에 등록을 하게 되고 현재 클래스컴포넌트의 인스턴스와 `setState`의 인자로 넘겼던 `partialState`를 인자로 넘기게 됩니다. 이때 `partialState`는 `fiber`에 담겨져 있다가 `reconciliation`이 끝나고 나면 state에 `Object.assign`으로 적용이 됩니다. ( 즉, 바로 state가 변경되지 않습니다. 중요한건 `reconciliation`이 끝나고 `state` 가 한번에 반영이 된다는 것입니다. )
- 그렇기 때문에 `setState` 를 연속으로 호출이 되면 전에 `setState` 호출 해서 얻은 결과가 뒤에 `setState` 에 반영이 되지 않는 것입니다. 그래서 `state`에 객체 대신에 함수 인자를 전달하는게 좋습니다. 

```javascript
<button onClick={
    () => {
        this.setState(prevState => {
            return {number: prevState.number + 1}
        }
    }
}>
</button>
```

- `this.setState`가 끝난 후 특정 작업 실행을 원한다면 `setState`의 두번째 파라미터로 콜백 함수를 등록하여 작업을 처리할 수 있습니다.
- 클래스형 컴포넌트든 함수형 컴포넌트든 `state`를 사용할 때는 주의해야할 사항은 state 값을 바꾸어야 할 때는 `setState` 혹은 `useState`를 통해 전달받은 세터 함수를 사용해야 하는 것입니다. 


### 참조 문서

- [State and Lifecycle](https://ko.reactjs.org/docs/state-and-lifecycle.html)



## Hooks (Function Component)
- Hooks는 리액트 v16.8에 새로 도입된 기능으로 함수형 컴포넌트에서도 상태 관리를 할 수 있는 uesState, 렌더링 직후 작업을 설정하는 useEffect 등의 기능을 제공하여 기존의 함수형 컴포넌트에서 할 수 없었던 다양한 작업을 할 수 있게 해줍니다.
- useState는 함수형 컴포넌트에서도 가변적인 상태를 지닐 수 있게 해줍니다.
- useEffect는 리액트 컴포넌트가 렌더링될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook이다. 클래스형 컴포넌트의 componentDidMount와 componentDidUpdate를 합친 형태로 보아도 무방합니다.

### Hooks 규칙
- 리액트 함수의 제일 상단에 작성해야합니다.
- 조건문, 내부 함수, 반복문 안에 사용하지 않습니다.
- 리액트 함수 안에서만 사용합니다.
- custom 함수 안에서는 예외적으로 호출 할 수 있습니다.

### 참조 문서
- [Hook의 개요](https://ko.reactjs.org/docs/hooks-intro.html)
- [React hooks: not magic, just arrays](https://medium.com/@ryardley/react-hooks-not-magic-just-arrays-cd4f1857236e)
- [How do React hooks really work?](https://www.netlify.com/blog/2019/03/11/deep-dive-how-do-react-hooks-really-work/)


# 전역 상태관리

## Context API
- 하나의 액션으로 해당하는 컴포넌트만 바꾸는게 아닌 다른 여러 컴포넌트도 바꾸고 싶을때 사용합니다.  ( one to many 관계 )
- context를 이용하면 단계마다 일일이 props를 넘겨주지 않고도 컴포넌트 트리 전체에 데이터를 제공할 수 있습니다.
- context의 주된 용도는 다양한 레벨에 네스팅된 많은 컴포넌트에게 데이터를 전달하는 것입니다.
- 같은 데이터를 모든 하위 컴포넌트에게 널리 "방송"이 필요할 때는 context가 유용하다.
- React 컴포넌트인 Provider는 context를 구독하는 컴포넌트들에게 context의 변화를 알리는 역할을 합니다.
- Consumer는 context 변화를 구독하는 React 컴포넌트입니다. 함수 컴포넌트안에서 context를 읽기 위해서 쓸 수 있습니다. Context.Consumer의 자식은 함수여야합니다. 이 함수는 context의 현재값을 받고 React 노드를 반환합니다.
- useContext를 쓰면 컴포넌트 함수 자체는 실행이 된다. 실제로 return 부분이 실행된다면 그게 실제로 re-rendering 되는 것이기 때문에 return 에 있는 부분만 캐싱을 해줘야 한다. useMemo 사용 ( 참고 : [https://www.youtube.com/watch?v=Y7m9RKmD0UQ](https://www.youtube.com/watch?v=Y7m9RKmD0UQ) )
- Context에 있는 값을 사용할 때 Consumer 대신 다른 방식을 사용하여 값을 받아 오는 방법은 useContext Hook 또는 class 컴포넌트에서 static contextType을 이용하는 방법이 있습니다.


```javascript
// context/color.js
import React, { createContext, useState } from 'react'
 
 
const ColorContext = createContext({
    state: { color: 'black', subcolor: 'red' },
    actions: {
        setColor: () => {},
        setSubcolor: () => {}
    }
})
 
 
const ColorProvier = ({ children }) => {
    const [color, setColor] = useState('black')
    const [subcolor, setSubcolor] = useState('red')
 
 
    const value = {
        state: {color, subcolor},
        action: {setColor, setSubcolor}
    }
 
 
    return (
        <ColorContext.Provider value={value}>{children}</ColorContext.Provier>
    )
 
 
}
 
 
const { Consumer: ColorConsumer } = ColorContext
export { ColorProvider, ColorConsumer }
 
 
export default ColorContext;
```

```javascript
// App.js
import React from 'react'
import ColorBox from './components/ColorBox'
import { ColorProvider } from './context/color'
 
 
const App = () => {
    return (
        <ColorProvider>
            <div>
                <ColorBox />
            </div>
        </ColorProvider>
    )
}
```

```javascript
// compoents/ColorBox.js
 
 
import React from 'react'
import { ColorConsumer } from '../contexts/color'
 
 
const ColorBox = () => {
    return (
        <ColorConsumer>
            {(state, action) => {
                (...)
            }}
        </ColorConsumer>
    )
}
 
 
export default ColorBox
```

### 참조 문서
- [Context API](https://ko.reactjs.org/docs/context.html)


# 실습 강의 

위 내용과 더불어 `Component Style`, `Routing` 실습까지 해볼 수 있는 실습 강의 

- [노마드 코더 (실습 동영상): 무료](https://academy.nomadcoders.co/courses/enrolled/216871)
- [ZeroCho React Youtube](https://www.youtube.com/watch?v=V3QsSrldHqI&list=PLcqDmjxt30RtqbStQqk-eYMK8N-1SYIFn)


