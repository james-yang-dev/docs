<!-- links -->
[prettierLink]: https://github.com/prettier/prettier-vscode
[asyncAwaitLink]: http://bitly.kr/qIJIDpg

# FE JavaScript Style Guide

## 개요

자바스크립트 코드는 이 가이드를 통해 상태를 평가하고 코드리뷰를 진행하게 됩니다.  
웹 개발에는 정말 많은 방식의 코드들이 있습니다. 프로젝트, 성격, 라이브러리, 개발자 등에 따라 바뀔 수 있으며, 심지어 한 사람이 작성한 코드가 다른경우도 종종 있습니다.  
프로젝트 기간동안 이 가이드를 준수함으로서 프로젝트간에 발생되는 혼란을 감소시키고, 표준화된 코드로 개발함으로서 많은 잇점을 얻을 수 있을 것 이라 생각됩니다.

## 기본 포맷

### 뒷자리 공백

맨 끝의 공백을 제거하세요.

불필요한 공백은 코드간 복잡한 충돌을 발생 시킵니다.  

**🚫 Not Recommended:**

``` javascript
const name = "John Smith";__
```

**✅ Recommended:**

``` javascript
const name = "John Smith";
```

[Prettier][PrettierLink]를 사용하여 자동으로 제거할 수 있습니다.

``` javascript
// 프레티어 내용 작성
```

### 들여 쓰기

들여쓰기는 전체의 파일에서 일관되게 적용되어야 합니다. 탭이나 공백 어느것을 사용해도 상관 없지만 일관성을 유지해야 합니다. `Tab`, `2 space`, `4 space`

[Prettier][PrettierLink]에서 들여쓰기를 일관되게 적용 해줍니다.

## 공통 정보

### Encoding

`UTF-8`을 사용해야 합니다.  

사용하는 개발 에디터에서 `UTF-8`을 사용하는지 확인하고 설정 해두어야 합니다.

### 주석

개발된 코드를 설명하는데 체계적인 주석을 사용하면 이력 관리에 많은 도움이 됩니다.
이 코드는 어느 부분에서 적용되는지, 어떤 목적으로 작성했는지, 어떤 해결 방식을 제시하거나 선호하는지에 대해 작성해야 합니다.

자바스크립트에 주석을 작성할 때 JSDocs 포맷을 이용합니다.  
이 모듈은 양식에 맞춰 작성하면 자동으로 변환해 프로젝트 전체의 주석을 문서화 해주는 유용한 툴 입니다.
JSDocs는 다양한 어노테이션을 사용할 수 있지만, 꼭 필요한 옵션만 사용하길 권장합니다.

- `@constructor:` 클래스의 컨스트럭터에 대한 설명을 작성합니다. `new` 를 사용해서 호출될때의 정의를 기술합니다.
- `@description:` 함수의 설명을 작성합니다. 이 태그에는 HTML마크업을 사용할 수 있습니다.
- `@param:` 함수에 사용된 파라미터의 타입, 이름, 그리고 설명에 대해 적습니다.
- `@returns:` 이 함수가 리턴하는 값의 타입과 설명에 대해 적습니다.

아래의 에제는 JSDocs를 어떻게 사용하는지에 대한 간단한 예시입니다.  

``` javascript
/**
* @description 책 정보 조회
* @constructor - do something in constructor
* @param {string} title - 책의 타이틀
* @param {string} author - 책의 저자
* @param {object} books - 타이틀과 저자로 조회된 책의 정보
*/
function Book(title, author) {
    return books
}
```

### 해야 될 일들

업무시간이 종료 되었거나, 사정에 의해 개발을 중단 할 때는 `TODO:` 를 사용하길 권장합니다.

`TODO:`를 사용할때는 다른 포맷을 사용하지 않고 아래의 방식으로만 사용하는것을 권장합니다.

**✅ Recommended:**

``` javascript
// TODO: 과일 갯수 구하는 기능 구현
```

## 자바스크립트 규칙

### 변수 선언

자바스크립트에는 3가지 방식의 변수 선언이 있습니다.

- const
- let
- var

변수를 선언할때 위에 3가지중 하나의 키워드를 사용하여 정의해야 합니다.  
기본적으로 `const` 를 사용합니다. 나중에 값을 재 할당해야 하는 경우에는 `let`을 사용합니다.  
`var`를 사용한 선언방식은 ES6 이상에서는 더이상 권장하지 않습니다.  

### 전역 변수

전역 변수는 복잡하고 어려운 버그들을 발생시키는 주 원인 중 하나입니다.  
가급적이면 사용하지 않습니다. 사용을 해야 될 경우에는 의도하지 않은 요인에 의해 오염되지 않도록 많은 주의를 기울여야 합니다.  
let, const를 이용해 블록 스코프를 적용하고, 클로져를 사용 하길 권장합니다.

**🚫 Not Recommended:**

전역으로 변수를 선언하면 의도치 않은 오염 발생의 가능성이 매우 높습니다.

``` javascript
var num = 0;

window.onload = function () {
    var num; // 중복 선언 발생
    alert(num); // undefined
    num = 5;
    alert(num);
}
```

**✅ Recommended:**

클로져는 좋은 대체 방법 중 하나 입니다.

``` javascript
var setNum = (function () {
  var counter = 0;
  return function (num) {
    counter = num;
    return counter;
  }
})();

function myFunction(){
  console.log(setNum(1))
}

setNum(2)
setNum(3)
```

### 세미콜론

세미콜론을 항상 사용해야 합니다.

요즘 개발 환경에서는 크게 문제되는 경우는 없지만, 다양한 환경을 고려하였을때 세미콜론을 항상 사용해야 합니다.  
세미콜론을 사용하지 않았을 때 복잡한 문제가 발생되는 경우가 있습니다.  
함수의 끝에는 사용하지 않지만, 화살표 함수의 끝에는 사용합니다.

**🚫 Not Recommended:**

``` javascript
const foo = () => {
    return true // Missing semicolon
} // Missing semicolon

function foo() {
    return true;
}; // Extra semicolon
```

**✅ Recommended:**

``` javascript
const foo = () => {
    return true;
};

function foo() {
    return true;
}
```

### 불필요한 래퍼 오브젝트의 사용

이유 없이 원시 자료형을 오브젝트로 감싸지 않아야 합니다. 이 방식은 위험성을 내포하고 있습니다.  
그렇지만 타입 캐스팅은 괜찮습니다.

**🚫 Not Recommended:**

``` javascript
const x = new Boolean(0);
if (x) {
    alert('hi');    // hi가 출력됩니다. typeof를 했을때 x는 boolean이 아니고 오브젝트로 인식됩니다
}
```

**✅ Recommended:**

``` javascript
const x = Boolean(false);
if (x) {
    alert('hi');    // hi가 출력되지 않습니다. x는 boolean으로 인식됩니다
}
```

### 클로져

클로져의 생성은 가장 유용하고 자주 사용되는 자바스크립트 기법입니다. 클로져를 사용할때는 하나만 염두해두면 됩니다.  
클로져의 포인터가 자신을 둘러싼 스코프 안에서만 유지된다는 사실 입니다.  
DOM 엘레멘트에 직접적으로 함수를 추가하면 순환 참조가 발생할 수 있고 메모리 누수가 발생됩니다.

**🚫 Not Recommended:**

``` Javascript
function foo(element, a, b) {
    element.onclick = function() { /* uses a and b */ }
}
```

**✅ Recommended:**

``` javascript
function foo(element, a, b) {
    element.onclick = bar(a, b);
}

function bar(a, b) {
    return function() { /* uses a and b */ }
}
```

### 비동기 처리

이전부터 활용되던 Ajax/callback, Promise들이 있지만 이제는 사용하지 않아야 합니다.  
Async/Await를 사용하여 비동기 호출을 처리합니다.  

Async/Await에 대한 설명은 [링크][asyncAwaitLink]로 대체 합니다.

### for와 for-in 그리고 forEach 반복문

**🚫 Not Recommended:**

``` javascript
myArray = ['a', 1, 'etc'];
for (const indexNum in myArray) {
    console.log(myArray[indexNum]);
}

const starWars = {
    "creatures": [
        {
            "name": "bantha",
            "face": "furry"
        },
        {
            "name": "loth-cat",
            "face": "toothy"
        }
    ]
};
for (const i in starWars.creatures) {
    console.log(starWars.creatures[i].name);
    console.log(starWars.creatures[i].face);
};
```

**✅ Recommended:**

``` javascript
mySimpleArray = ['a', 1, 'etc'];
mySimpleArray.forEach(function(val) {
    console.log(val);
});

const starWars = {
    "creatures": [
        {
            "name": "bantha",
            "face": "furry"
        },
        {
            "name": "loth-cat",
            "face": "toothy"
        }
    ]
};
starWars.creatures.forEach(function(creature) {
    console.log(creature.name);
    console.log(creature.face);
});
```

### Array

배열의 반복문을 처리할때 **for-in** 보다는 **forEach** 나 **for** 반복문을 사용해서 처리합니다.

**🚫 Not Recommended:**

``` javascript
myArray = ['a', 1, 'etc'];
for (const indexNum in myArray) {
    console.log(myArray[indexNum]);
}

const starWars = {
    "creatures": [
        {
            "name": "bantha",
            "face": "furry"
        },
        {
            "name": "loth-cat",
            "face": "toothy"
        }
    ]
};
for (const i in starWars.creatures) {
    console.log(starWars.creatures[i].name);
    console.log(starWars.creatures[i].face);
};
```

**✅ Recommended:**

``` javascript
mySimpleArray = ['a', 1, 'etc'];
mySimpleArray.forEach(function(val) {
    console.log(val);
});

const starWars = {
    "creatures": [
        {
            "name": "bantha",
            "face": "furry"
        },
        {
            "name": "loth-cat",
            "face": "toothy"
        }
    ]
};
starWars.creatures.forEach(function(creature) {
    console.log(creature.name);
    console.log(creature.face);
});
```

// 또는

``` javascript
myArray = ['a', 1, 'etc'];
for (let indexCount = 0; indexCount < myArray.length; indexCount++) {
    console.log(myArray[indexCount]);
};
```

### 전개연산자

배열 값을 사용할때 좀 더 직관적으로 사용할 수 있는 방법 입니다.  

**🚫 Not Recommended:**

``` javascript
function add(a, b, c){
    return a+b+c;
}
var arr = [2, 4, 5];
add.apply(null, arr);
// 11
```

``` javascript
var arr1 = [1, 2, 3];
var arr2 = [4, 5, 6];

Array.prototype.push.apply(arr1, arr2);
// [1, 2, 3, 4, 5, 6]
```

**✅ Recommended:**

``` javascript
const add = (a, b, c) => {
    return a+b+c;
}
var arr = [2, 4, 5];
add(...arr);
// 11
```

``` javascript
var arr1 = [1, 2, 3];
var arr2 = [4, 5, 6];

arr1.push(...arr2);
// [1, 2, 3, 4, 5, 6]
```

``` javascript
var arr1 = [3, 4, 5];
var arr2 = [1, 2, ...arr1, 6, 7];
console.log(arr2);
// [1, 2, 3, 4, 5, 6, 7]
```

### 구조 분해 할당(디스트럭처링)

어느 변수를 선언하고 값을 할당 할 때는 정해진 순서가 있습니다.  
우선 변수를 선언(1) 하고 할당(2) 하는 단계를 거쳐야 합니다.  
변수 한 두개 정도는 간단히 작업할 수 있지만, 전달 받은 객체의 값들을 재 할당하는 과정은 그리 녹록치 않습니다.

아래 구조 분해 할당을 통해 더 쉽고 정확하게 변수를 선언하고 값을 할당할 수 있습니다.

**🚫 Not Recommended:**

``` javascript
var arr = [1, 2, 3];

var one   = arr[0];
var two   = arr[1];
var three = arr[2];

console.log(one, two, three); // 1 2 3
```

``` javascript
var obj = { firstName: 'james', lastName: 'yang' };

var firstName = obj.firstName;
var lastName  = obj.lastName;

console.log(firstName, lastName); // james yang
```

**✅ Recommended:**

``` javascript
const arr = [1, 2, 3];

const [one, two, three] = arr;

console.log(one, two, three); // 1 2 3
```

``` javascript
const obj = { firstName: 'james', lastName: 'yang' };

const { lastName, firstName } = obj;

console.log(firstName, lastName); // james yang
```

### 오브젝트

<!-- 번역 추가 필요? -->
for-in 반복문은 오브젝트의 키에 접근할 수 있지만, 값에는 접근할 수 없습니다.  
또한 for-in은 Array가 가지고 있는 내장함수들에도 프로토 타입 체인을 통해 접근할 수 있으며 이 기능은 많은 문제를 초래할 수 있습니다.

for-in을 사용하지 않고 for-of 를 사용하여 처리하길 권장합니다.

**🚫 Not Recommended:**

``` javascript
myObj = {'firstName':'Ada','secondName':'Lovelace'};
for (const key in myObj) {
    console.log(myObj[key]);
}
```

**✅ Recommended:**

``` javascript
myObj = {'firstName':'Ada','lastName':'Lovelace'};
for (const key in myObj) {
    if (myObj.hasOwnProperty(key)) {
        console.log(myObj[key]);
    }
}
```

### 여러 줄의 문자열

사용하지 마십시오.  

특수기호를 통해 문자열 안에서 개행을 처리하는 방식은 에러를 유발할 수 있습니다.
문자열끼리 더하는 방식을 사용하거나, 리터럴 방식을 사용해서 여러 줄의 문자열을 표시하는것이 좋습니다.  
ES6이상에서는 사실 리터럴 방식을 사용하는것이 가장 좋습니다.

**🚫 Not Recommended:**

``` javascript
const myString = 'A rather long string of English text, an error message \
    actually that just keeps going and going -- an error \
    message that is really really long.';
```

``` javascript
const myString = 'A rather long string of English text, an error message' +
    'actually that just keeps going and going -- an error' +
    'message that is really really long.';
```

**✅ Recommended:**

``` javascript
const myString = `A rather long string of English text, an error message
    actually that just keeps going and going -- an error
    message that is really really long.`;
```

### 배열과 오브젝트의 값

배열과 오브젝트의 컨스트럭터를 사용하지 않는 대신에 그냥 값을 대입하기를 권장합니다.

**🚫 Not Recommended:**

``` javascript
const myArray = new Array(x1, x2, x3);

const myObject = new Object();
myObject.a = 0;
```

**✅ Recommended:**

``` javascript
const myArray = [x1, x2, x3];

const myObject = {
    a: 0
};
```

## 자바스크립트 스타일 규칙

### 이름짓기

보편적으로 정해진 대로 대소문자 구문을 합니다.

- 함수(method 포함), 변수 : nameLikeThis
- 클래스 : ClassNameLikeThis
- 상수 : CONSTANT_VALUE_LIKE_THIS
- 파일명 : filenamelikethis.js

### 코드 형식

세미콜론을 넣는 라인은 대괄호로 감싸 줍니다. 같은 라인에 표시하지 않고 기본적으로 개행 합니다.  

**✅ Recommended:**

``` javascript
if (something) {
    // Do something
} else {
    // Do something else
}
```

한 줄일 경우에는 한 라인에 표시합니다.  

**✅ Recommended:**

``` javascript
const array = [1, 2, 3];
const object = {a: 1, b: 2, c: 3};
```

여러 줄의 배열이나 오브젝트를 초기화 할 때는 아래와 같이 개행합니다. 줄의 구분은 쉼표로 처리하고, 오브젝트나 배열을 닫을때 역시 같은 방식으로 처리합니다.

**✅ Recommended:**

``` javascript
const array = [
    'Joe <joe@email.com>',
    'Sal <sal@email.com>',
    'Murr <murr@email.com>',
    'Q <q@email.com>'
];

const object = {
    id: 'foo',
    class: 'foo-important',
    name: 'notification'
};
```

### 문자열 - String

'(싱글) 와 "(더블)는 서로를 문자열로 취급합니다. 아래의 예제를 통해 확인해보세요.  
자바스크립트에서는 기본적으로 '(싱글)을 사용하여 문자열 처리를 합니다.

**✅ Recommended:**

```javascript
const element = '<button class="btn">Click Me</button>';
```

** 다만 JSON에서는 문법상 " 만 허용합니다.

## Tips and Tricks

### 참과 거짓 검증에 대한 정리

아래의 경우에 자바스크립트는 거짓으로 판단을 합니다

- null
- undefined
- '' the empty string
- 0 the number

그러나, 아래의 경우에는 참으로 판단 합니다.

- '0' 문자열일 경우
- [] 빈 배열일 경우
- {} 빈 오브젝트 일 경우

### 삼항연산

단순 비교일때는 삼항연산을 통해 코드를 줄이는 걸 권장합니다.

단순 검증일 경우에는 삼항연산을 통해 코드를 줄일 수 있습니다.  
2개 이상의 선택지가 필요한경우에는 삼항연산을 사용하지 마십시오.

아래 코드 예시를 확인하세요.

**🚫 Not Recommended:**

```javascript
if (val) {
    return foo();
} else {
    return bar();
}
```

**✅ Recommended:**

```javascript
return val ? foo() : bar();
```

### && 와 ||

삼항 연산 또는 다른 비교에서 항상 &&와 ||를 사용해야 합니다.

**🚫 Not Recommended:**

```javascript
const foo = (name) => {
    const theName;
    if (name) {
        theName = name;
    } else {
        theName = 'John';
    }
};
```

**✅ Recommended:**

```javascript
const foo = (name) => {
    const theName = name || 'John';
};
```

`&&` 역시 같은 방식으로 사용할 수 있습니다. 코드가 짧아지고 여러 잇점이 있습니다.

**🚫 Not Recommended:**

```javascript
if (node) {
    if (node.kids) {
        console.log(node.kids);
    }
}
```

**✅ Recommended:**

```javascript
if (node && node.kids) {
    console.log(node.kids);
}
```

### == 와 ===

값을 비교할때는 ===(엄격비교)를 사용하길 권장합니다.  
자바스크립트에서 처리되는 많은 예외사항들 때문에 ==(간단비교)를 하게 되면 검증을 제대로 하지 못할때가 많습니다.

**🚫 Not Recommended:**

```javascript
const testString = '1'
const testNumber = 1

if (testString == testNumber) {
    console.log('is true');
} else {
    console.log('is false');
}
```

엄격하게는 문자열 '1' 과 숫자 1은 다르지만, 자동으로 변환되어 값만 비교 됩니다.

**✅ Recommended:**

```javascript
const testString = '1'
const testNumber = 1

if (testString === testNumber) {
    console.log('is true');
} else {
    console.log('is false');
}
```

엄격 비교를 하면 타입까지 비교를 하게 됩니다.
