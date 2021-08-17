# 입점신청서
## 개요
  샵 입점서 양식을 활용해서 양식은 건드리지 않고 신청서만 추가 생성하는 문제입니다.
  1. 2명의 입점자를 생성한다. 입점자 양식은 class ShopInfo와 동일해야 한다.
  2. 입점자의 id는 숫자만 입력할 수 있으며 아무 숫자나 가능하다.
  3. 각 입점자는 해당 내용들을 기입한다. 입점자의 ID나 size, type은 중복될 수 있다.
  4. 유효성 검증은 클래스 내의 isSize를 통해 사이즈를, 타입은 isType을 통해 타입에 대한 검증을 한다.
  5. 지정된 신청양식의 속성외에는 값을 넣을 수 없다. 예) shopInfo.testProps = 5 안됨.
  6. 신청이 완료되면 신청서는 더 이상 수정되지 않도록 처리해야 한다
  7. 모든 신청이 완료되면 완료된 신청서를 출력한다.


## 설명
- 기능 설명
- A 빌딩 몇 개의 상가가 비어있다.
- 입점 공고를 통해 몇 명의 입점희망자가 입점 신청을 한다.
- 입점 신청자는 id, size, type을 기재하고 신청한다.

```javascript
// 이 클래스는 수정할 수 없다.
class ShopInfo {
  constructor() {
    const sizeList = [10, 20, 30]
    const typeList = ['resturant', 'pharmacy', 'fashion', 'cafe']

    this.id = 0
    this.size = 0
    this.type = ''
    this.complete = false

    this.isSize = value => sizeList.includes(value)
    this.isType = value => typeList.includes(value)
  }
}

function init() {
    
}

init()


```

## 출제의도
1. 자바스크립트의 클래스에 대해 이해하고 있는지 확인합니다.
2. 클래스를 확장, 재정의 할 수 있는 다양한 패턴에 대해 알고 있는지 확인합니다.
3. 클래스의 값을 핸들링함에 있어 클래스 함수를 통해 접근하고 제어하는지 확인합니다.

## 채점기준
1. 가장 중점적인 부분은 입력에 대한 검증 및 정보 저장에 있다. 
2. 입점자를 생성하고, 출력하는 부분은 프로그램의 시작과 끝에 구현하는것 만으로 충분하다.
3. 신청서의 상태값에 따라서 해당 신청서가 더 이상 수정되지 않도록 하는 부분은 반드시 구현해야 한다.

## 답안 유형
### 프록시 핸들러를 통해 기존 클래스(양식)를 손대지 않고 확장 가능하게 구현 했습니다.
```javascript
class Shop {
  constructor() {
    this.size = [10, 20, 30]
    this.rent = [40, 70, 110]
    this.shopType = ['resturant', 'pharmacy', 'fashion', 'cafe']
  }
}

const shopHandler = {
  get: (obj, name, receiver) => {
    const complete = 'complete'
    if (name === complete) {
      return obj[complete] === undefined ? false : obj[complete]
    } else if (name === 'orgSize') {
      console.log(obj)
      // return Reflect.get(obj, complete, receiver)
    }
    console.log(name)
    return Reflect.get(obj, name, receiver)
  },
  set: (obj, prop, value) => {
    const complete = 'complete'
    if (!obj[complete]) {
      if (prop === complete && value === true) {
        obj[prop] = value
      } else if (prop === 'id' && !isNaN(value)) {
        obj[prop] = value
      }
    } else {
      console.log(`this obj was completed!`)
    }

    return true
  }
}

function init() {
  const testHandler = new Proxy(Shop, shopHandler)
  const shopObj = new Shop()

  console.log(testHandler)
  testHandler.complete = true

  console.log(testHandler.size)
}

init()


```
