# 메뉴 정리
## 개요
  조건에 맞춰 버튼의 기능들을 정의하는 문제입니다. 이 문제는 알고리즘이나 해결과정보다는 프로그래밍에 얼마나 익숙하지를 확인합니다.
  1. 가격 필터를 구현합니다. 버튼을 누르면 입력된 가격 이하만 메뉴에 표시되도록 합니다.
  2. 가격 세일을 구현합니다. 버튼을 누르면 메뉴 전체의 가격이 지정된 세일 % 기준으로 가격이 표시됩니다.
  3. 메뉴 추가를 구현합니다. 버튼을 누르면 가격과 메뉴명을 입력받아 메뉴에 추가합니다.
  4. 기능별 버튼을 구현합니다. 메뉴순(id), 가격 오름차순, 초기화 를 누르면 각 기능을 수행합니다.
  5. 각 기능을 구현하며 이미 구현된 요소를 직접 수정할 수 있고, 함수 자체도 전부 변경할 수 있습니다. 실제 코드를 작성하는 방식으로 유도되어야 합니다.

```html
<html>
<body>

<div>
  <ul id="menuList">
  </ul>
</div>
<div>
  <input type="number" id="inputFilterPrice" placeholder="원 단위로 입력">
  <button onClick="onClickFilter()">
  가격 필터
  </button>
</div>
<div>
  <input type="number" id="inputSalePercent" placeholder="%단위로 입력">
  <button onClick="onClickSale()">
  가격 세일
  </button>
</div>
<div>
  <span>가격</span>
  <input type="number" id="inputMenuPrice" placeholder="원 단위로 입력">
  <span>메뉴명</span>
  <input type="text" id="inputMenuName" placeholder="메뉴명 입력">
  <button onClick="onClickAddMenu()">
  메뉴 추가
  </button>
</div>
<br>
<div>
  <span>메뉴 정렬</span>
  <button onClick="onClickSort('menu')">
  메뉴 순
  </button>
  <button onClick="onClickSort('price')">
  가격 오름차순
  </button>
  <button onClick="onClickReset()">
  초기화
  </button>
</div>

</body>
</html>
```
```javascript
const menuList = [
  {
    menuId : 1,
    menuName : '아메리카노',
    price: 1000
  },
  {
    menuId : 3,
    menuName : '카페 라떼',
    price: 2500
  },
  {
    menuId : 4,
    menuName : '카페 모카',
    price: 3500
  },
  {
    menuId : 2,
    menuName : '카페 모카',
    price: 2500
  }
];

const onClickFilter = () => {
  // 입력된 가격 이하만 표시되도록 수정
}

const onClickSort = () => {
  // 입력된 기준 순으로 정렬
  // 메뉴순은 메뉴 id 순서대로 정렬된다
}

const onClickReset = () => {
  // 초기화를 수행한다
}

const onClickSale = () => {
  // 가격을 입력된 내용만큼 수정한다.
}

const onClickAddMenu = () => {
  // 가격과 메뉴명을 받아 새로 메뉴를 추가한다.
}


function init() {
  const menuListViewer = document.querySelector('#menuList');
  menuList.map(menu => {
    const liObject = document.createElement('LI');
    liObject.id = menu.menuId;
    liObject.innerHTML = menu.menuName + ' : ' + menu.price;
    menuListViewer.appendChild(liObject);
  });
}

init();
```

## 출제의도 및 검증 기준

### 데이터의 불변성을 지키는지

- 필터나 정렬 등의 기능을 수행할 때 원본에 직접 수정을 가하지 않아야 한다.
- 오브젝트의 값을 업데이트 하는 방식에 대해 이해하고 있는지.

### 함수형 프로그래밍의 특성을 이해 하는지

- 파라미터로 넘어온 데이터는 원본 값을 항상 유지하여야 한다. 
- 함수는 한 가지의 역할만 수행하도록 작성되는지, 항상 동일한 결과를 리턴할 수 있도록 해야 한다.

### 코드의 품질

- 코드를 작성하는 방식이 일관되는지 확인한다. var, let, const 의 사용방식 개행의 방식이나 삼항연산, 반복문의 사용, ; 의 사용 여부등의 일관성을 확인한다.
- 틀린 내용이 아니면 기존 코드의 작성 방식을 따르는지 확인한다. 이는 협업에 대한 경험, 이해도를 나타낸다.
- 적절하지 않은 코드를 가독성이나 효율성 위주로 리팩토링 할 수 있는지. literal 방식의 사용 이해


## 답안 유형

답안 링크  
[기초]:(https://jsfiddle.net/carlos_yang/9cfug8zb/1/)  
[중급]:(https://jsfiddle.net/carlos_yang/q3257Ley/2/)

이 테스트는 어디까지나 문제 해결을 하는 과정을 보기 위함입니다.  
라이브 테스트에서는 정상 동작하지 않을 수 있지만, 의미가 맞고 큰 실수가 없다면 이 부분이 감점 요인이 되어서는 안될것입니다.

### 기초

각 버튼의 기능들을 구현하면서 불변성을 유지하고, 오브젝트를 다루는 함수들을 잘 이해하고 있는지 확인합니다.  
각각의 기능들이 원본 데이터를 유지한 상태에서 표시되는 데이터를 조작하는지를 중점적으로 확인합니다.  
메뉴 추가시나 초기화시에 기능 동작에 대한 룰 정의가 필요한데, 이 부분은 가이드가 되어야 할 내용입니다.  
보통의 구현으로는 메뉴 추가시에 필터링, 세일, 정렬이 정상적으로 적용되지 않을 가능성이 많습니다. 이 부분은 기초에서 다룰 수 있는 내용은 아니라고 판단되며, 해당 내용은 아래 중급에서 확인하면 될 것 같습니다.  

```javascript
const menuList = [
  {
    id: 1,
    name: '아메리카노',
    price: 1000,
  },
  {
    id: 3,
    name: '카페 라떼',
    price: 2500,
  },
  {
    id: 4,
    name: '카페 모카',
    price: 3500,
  },
  {
    id: 2,
    name: '플랫화이트',
    price: 2800,
  },
];

let salePercent = 0;

const setSalePercent = (percent = 0) => {
  salePercent = parseInt(percent);
};

const getMenuPrice = (price = 0) => price - (price * salePercent) / 100;

// 메뉴리스트 표시할 데이터를 받아서 그대로 표시해준다.
const setMenuList = (menuData) => {
  const menuListViewer = document.querySelector('#menuList');
  while (menuListViewer.firstChild) {
    menuListViewer.firstChild.remove();
  }

  menuData.map((menu) => {
    const liObject = document.createElement('LI');
    liObject.id = menu.id;
    liObject.innerHTML = menu.name + ' : ' + menu.price;
    menuListViewer.appendChild(liObject);
  });
};

// 필터 클릭시 구현
const onClickFilter = () => {
  const filterPrice = document.querySelector('#inputFilterPrice').value;
  const filteredMenuList = menuList.filter((menu) => menu.price <= filterPrice);
  setMenuList(filteredMenuList);
};

// sort 클릭시 구현
const onClickSort = () => {
  const sortMenuList = menuList.slice().sort(function sortWithPrice(a, b) {
    return a.price - b.price;
  });
  setMenuList(sortMenuList);
};

// 리셋시 초기화
const onClickReset = () => {
  setMenuList(menuList);
  setSalePercent(0);
};

// sale 버튼 클릭시 구현
const onClickSale = () => {
  const inputSalePercent = document.querySelector('#inputSalePercent').value;
  setSalePercent(inputSalePercent);
  const saleMenuList = menuList.map((menu) => {
    return { ...menu, price: getMenuPrice(menu.price) };
  });
  setMenuList(saleMenuList);
};

const onClickAddMenu = () => {
  const inputMenuPrice = document.querySelector('#inputMenuPrice').value;
  const inputMenuName = document.querySelector('#inputMenuName').value;

  if (!inputMenuPrice || !inputMenuName) {
    console.log('메뉴 가격, 이름을 입력해주세요');
    return false;
  } else {
    const menuIdList = menuList.map((menu) => menu.id);
    const nextMenuId = Math.max(...menuIdList) + 1;
    const newMenu = {
      id: nextMenuId,
      name: inputMenuName,
      price: inputMenuPrice,
    };
    menuList.push(newMenu);
  }
};

function init() {
  setMenuList(menuList);
}

init();
```

### 중급이상

메뉴 데이터를 표시하는 과정에서 적용되어야 할 데이터 변형을 함수형으로 구현할 수 있는지가 중점입니다.  
각 메뉴를 조작하는 기능들은 상태값을 가지고 있고, 화면에 데이터 표시시에 일괄적으로 표현될 수 있도록 되어있습니다.  
각각의 기능들은 데이터를 직접 조작하지 않는것이 핵심입니다.  

```javascript
const menuList = [
  {
    id : 1,
    name : '아메리카노',
    price: 1000
  },
  {
    id : 3,
    name : '카페 라떼',
    price: 2500
  },
  {
    id : 4,
    name : '카페 모카',
    price: 3500
  },
  {
    id : 2,
    name : '플랫화이트',
    price: 2800
  }
];

// 상태관리값으로 사용되는 
let useSalePercent = 0;
let useFilterPrice = 0;
let useSortType = '';

// 메뉴 가격을 구해주는 함수. 숫자로 넘어오는 데이터를 %로 계산해서 리턴한다.
const getMenuPrice = (price = 0) => price-(price * useSalePercent / 100);

// 메뉴 할인 함수
const menuSale = menuData => {
  const saleMenuList = menuList.map(menu => {
    return {...menu, price: getMenuPrice(menu.price)};
  });
  return saleMenuList;
}

// 메뉴 필터링 함수
const menuFilter = menuData => menuData.filter(menu => menu.price <= useFilterPrice);

// 메뉴 정렬 함수
const menuSort = menuData => {
  let resultMenuList;
  if('menu' === useSortType) {
    resultMenuList = menuData.slice().sort(function sortWithId(a, b) {
      return a.id - b.id;
    });
  } else if ('price' === useSortType) {
    resultMenuList = menuData.slice().sort(function sortWithPrice(a, b) {
      return a.price - b.price;
    });
  }
	
  return resultMenuList ? resultMenuList : menuData;
}

/* 메뉴 리스트를 표시하는 함수.
1. 리스트가 보여지는 UL을 항상 초기화
2. 데이터 변형이 가해지는 순서를 정의. 각각의 변형은 필요시에만 동작한다. sale -> filter -> sort
3. 변형된 데이터를 화면에 표시. 
*/
const setMenuList = () => {
  const menuData = menuList;
  const menuListViewer = document.querySelector('#menuList');
  
  while(menuListViewer.firstChild) {
    menuListViewer.firstChild.remove();
  }
  
  const saleMenu = useSalePercent > 0 ? menuSale(menuData) : menuData;
  const filteringMenu = useFilterPrice > 0 ? menuFilter(saleMenu) : saleMenu;
  const sortMenu = useSortType !== '' ? menuSort(filteringMenu) : filteringMenu;
  
  sortMenu.map(menu => {
    const liObject = document.createElement('LI');
    liObject.id = menu.id;
    liObject.innerHTML = menu.name + ' : ' + menu.price;
    menuListViewer.appendChild(liObject);
  });
}

// 세일 버튼 클릭시 구현
const onClickSale = () => {
  const intSalePercent = parseInt(document.querySelector('#inputSalePercent').value);
  useSalePercent = isNaN(intSalePercent) ? 0 : intSalePercent;
  setMenuList();
}

// 필터 버튼 클릭시 구현
const onClickFilter = () => {
  const intFilterPrice = parseInt(document.querySelector('#inputFilterPrice').value);
  useFilterPrice = isNaN(intFilterPrice) ? 0 : intFilterPrice;
  setMenuList();
}

// 정렬 버튼 클릭시 구현
const onClickSort = sortType => {
  useSortType = sortType;
  setMenuList();
}

// 상태값들을 리셋한다
const resetParams = () => {
  useSalePercent = 0;
  useFilterPrice = 0;
  useSortType = '';
}

const onClickReset = () => {
  resetParams();
  setMenuList();
}

// 메뉴를 추가한다.
const onClickAddMenu = () => {
  const inputMenuPrice = document.querySelector('#inputMenuPrice').value;
  const inputMenuName = document.querySelector('#inputMenuName').value;
  
  if(!inputMenuPrice || !inputMenuName) {
    console.log('메뉴 가격, 이름을 입력해주세요');
    return false;
  } else {
    const menuIdList = menuList.map(menu => menu.id);
    const nextMenuId = Math.max(...menuIdList) + 1;
    const newMenu = {
      id : nextMenuId,
      name: inputMenuName,
      price: inputMenuPrice
    };
    menuList.push(newMenu);
  }
  setMenuList(menuList);
}


function init() {
  setMenuList();
}

init();
```
