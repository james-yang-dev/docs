# Simple Local Rest Server

JSON 포맷을 기준으로 임시 서버를 만드는것이 목표 이다.  
로컬에서 사용하거나, 임시 서버로 사용하기 위함이 목적이기 때문에 복잡하지 않게 구성하는 것이 주안점이다.

## 설치 과정

### 사용 모듈

아래의 모듈들이 사용되었으며, package에 추가를 해 주어야 한다.

- [JSON-Server](https://www.npmjs.com/package/json-server)
- [lowdb](https://www.npmjs.com/package/lowdb)
- [nodemon](https://www.npmjs.com/package/nodemon)
- [shortid](https://www.npmjs.com/package/shortid)
- [body-parser](https://www.npmjs.com/package/body-parser)

<details>
<summary>모듈 요약 정보</summary>

#### JSON-Server

json 구조의 파일을 이용해 DB처럼 사용하는 간단한 테스트 서버이며, id를 이용한 기본적인 CRUD를 제공한다.

#### lowdb

함수를 통해 간단하게 DB를 제어할 수 있게 해주는 모듈이다. 이 문서에선 모든 데이터 조작이 lowdb를 통해 이뤄진다.  
[lowdb 참조 문서](https://github.com/typicode/lowdb)

#### nodemon

router를 생성하고 수정할때 바로 node를 재 시작하도록 해주는 데몬

#### shortid

unique한 아이디를 생성하게 해주는 모듈. lowdb에는 id를 생성하는 기능이 없기 때문에, db에 새로 데이터를 주입시 임시의 id를 생성할 수 있다.

#### body-parser

request를 통해 넘어오는 body의 데이터를 파싱하기 위한 모듈. request.body를 통해 간편하게 전달되는 데이터들을 추출할 수 있다.

</details>

## DB 서버

### db.json

db의 스키마가 될 json 파일을 의미한다. 보통 사용되는 json 형식과 완전히 동일하다.

<details>
  <summary>db.json 파일 예제</summary>
  
  ```json
  {
  "users": [
    {
      "id": "tester1",
      "password": "tester12",
      "email": "tester1@tester.com"
    },
    {
      "id": "tester2",
      "password": "tester123",
      "email": "tester2@tester.com"
    },
  ],
  "todos": [
    {
      "id": "todo0101",
      "postUserId": "tester2",
      "article": "tester 2 registered",
      "date": "2010-01-20"
    },
    {
      "id": "todo0102",
      "postUserId": "tester1",
      "article": "tester 1 registered",
      "date": "2010-01-22"
    },
  ]
  }
  ```

</details>

### server.js

실제 node를 통해서 서비스 될 서버를 의미한다. 한 공간에 필요한 파일들을 모아둔다.(server.js, db.json 등)  
이 문서에서는 **/src/data/** 밑에 위치한다.

```javascript
// json 파일을 db로 사용하기 위한 서버 선언
const jsonServer = require('json-server')
// db를 조작하기 위한 lowdb 선언
const low = require('lowdb')

const bodyParser = require('body-parser')
const shortid = require('shortid')

// 파일을 동기화로 다루기 위한 파일 싱크 선언, lowdb의 어댑터 모듈중 하나이다.
const FileSync = require('lowdb/adapters/FileSync')

const server = jsonServer.create()
// 대상이 되는 json파일을 지정한다.
const router = jsonServer.router('./db.live.json')
const middlewares = jsonServer.defaults()

// 관리를 위한 파일 싱크를 지정한다.
const adapter = new FileSync('src/data/db.live.json')
const db = low(adapter)

server.use(middlewares)
server.use(bodyParser.json())

/*
이 사이에 router의 내용을 구현한다. 아래 참조
*/

server.use(router)

server.listen(7979, () => {
  console.log('JSON Server is running')
})

```

package.json에는 아래처럼 사용 한다

```json
 "scripts": {
    "api": "nodemon src/data/server.js",
  }
```
npm을 통한 사용
```bash
npm run api
```

### router 정의

router를 통해 넘어오는 url 및 method, request들을 정의한다. 서버 파일안에 위치하며, 기능이 많아지는 경우 별도의 라우터로 관리하는편이 좋다.  
이 문서에선 server.js안에 기록한다.

#### 일반 조회

```javascript
// get method의 정의 방식
server.get('/users', (req, res) => {
  // db.get(domain) 을 통해 값을 조회한다.
  // json 파일 안에 선언된 object를 의미함.
  const userData = db.get('users').value()
  // response를 통해 조회된 값을 전달한다.
  res.send(userData)
})
```

#### 파라미터 조회

일반적으로 사용되는 배열 함수를 그대로 사용한다.

**find** : 1개 조회(가장 첫번째가 조회됨)

```javascript
server.get('/users/:id', (req, res) => {
  // 위에 :id 로 표시된 부분을 파라미터로 받는다.
  const userId = req.params.id
  const userData = db
    .get('users')
    // object 형태로 전달해서 값을 확인한다.
    .find({ id: userId })
    .value()
  res.send(userData)
})
```

**filter** : 조건에 맞는 값 전부 조회

```javascript
server.get('/users/:id', (req, res) => {
  const userId = req.params.id
  const userData = db
    .get('users')
    // filter 함수를 사용해서 일치되는 값 전부를 조회한다
    .filter({ id: userId })
    .value()
  res.send(userData)
})
```

```javascript
server.get('/todos/user/:groupId', (req, res) => {
  const groupId = req.params.groupId

  // 그룹에 속한 유저 전부 조회
  const userList = db
    .get('group')
    .filter({ id: groupId })
    .value()
  // user id만 배열로 추출
  const userIdList = userList.map(user => user.id)

  const todoData = db
    .get('todos')
    // 2개 이상의 값을 파라미터로 전달할때 사용하는 방식
    .filter(todo => userIdList.findIndex(todo.userId) > -1)
    .value()
  res.send(userData)
})
```

body를 통해 data가 넘어오는경우의 사용방식 post, put, patch 등

```javascript
server.post('/users', (req, res) => {
  // body-parser를 통해 파싱된 request의 body에서 바로 값을 꺼낸다.
  const userId = req.body.userId
  const userPw = req.body.userPw

  const userData = db
    .get('users')
    .find({ id: userId, password: userPw }) // find를 통해 값을 검색한다.
    .value()

  res.send(userData)
})
```

#### 데이터 핸들링

**update** : 검색된 결과에 assign을 이용한다.

```javascript
server.patch('/user', (req, res) => {
  const updateData = req.body.userData
  const userData = db
    .get('users')
    .find({ id: updateData.id }) // 수정 전에 필요한 데이터를 find를 이용해 추출한다.
    .assign({
      // assign을 통해 수정한다
      name: updateData.name,
      join: true
    })
    .write() // write를 통해 조작된 데이터를 덮어쓴다.

  res.send(todoData)
})
```

**insert** : db를 조회하고 push를 이용한다.

```javascript
server.put('/todo', (req, res) => {
  const inputData = req.body.todoData

  const todoData = db
    // 입력할 domain을 선택한다
    .get('todos')
    // 필요한 데이터를 push해서 입력 한다.
    .push({
      id: shortid.generate(),
      userId: '',
      done: inputData.done
    })
    .write()

  res.send(todoData)
})
```

**delete** : 선택된 데이터를 삭제한다

```javascript
server.delete('/todo', (req, res) => {
  const inputData = req.body.todoData

  const todoData = db
    .get('todos')
    // 조건에 맞는 데이터를 삭제한다.
    .remove({ id: inputData.id })
    .write()

  res.send(todoData)
})
```

이 외에 자세한 내용은 [lowdb 문서](https://github.com/typicode/lowdb)를 참고한다.

---

##### 서버의 구성은 여기까지 이며, 서버의 구축만이 목적이면 아래의 내용을 확인하지 않아도 된다

---

## Client

이 내용은 프론트엔드 개발에서 사용되는 방식의 예를 나타낸다.

### Axios

이 문서에서는 **axios**를 사용해서 호출하는 모듈을 만든다.  
아주 간단한 예제이며, 실 사용과는 차이가 있다는 점을 알아둬야 한다.

#### index.js

```javascript
const API_URL = 'http://localhost:7979/'

// 외부에서 api를 호출하게 될때 사용하는 request 생성 모듈
// 호출시 필요한 config 정보를 전달해준다.
const createRequest = config => {
  const instance = axios.create()
  instance.defaults.headers['Accept'] = 'application/json'
  instance.defaults.headers['Content-Type'] = 'application/json'
  instance.defaults.baseURL = API_URL

  // 필요시 권한 처리 등도 여기나 인터셉터에서 핸들링 한다.

  // api 호출 정보를 config를 통해 전부 전달 받는다.
  return (
    instance(config)
      // 성공시
      .then(res => Promise.resolve(res.data))
      // 에러시
      .catch(err => {
        console.log(err)
        return Promise.reject({ err: err })
      })
  )
}

export default createRequest
```

### API.js

URL호출은 API의 정보를 다루는 모듈에서 이뤄진다.

#### user.api.js

method : **get**

```javascript
import createRequest from './index'

const getUserList = () => {
  // request를 보낼 정보를 config에 지정한다.
  const REQUEST_CONFIG = {
    // 메소드의 형식
    method: 'get',
    // 호출할 url
    url: 'users'
    // 파라미터 사용시는 url 뒤에 일반적인 파라미터 형태로 붙여준다.
    url: 'users?test=7&userId=35'
  }
  return createRequest(REQUEST_CONFIG)
}
```

method : **post**, **put**, **patch** 등 Data를 Body로 전달하는 방식

```javascript
import createRequest from './index'

const getUserList = authData => {
  const REQUEST_CONFIG = {
    method: 'post',
    url: 'users',
    // body를 통해 전달할 데이터
    data: {
      userInfo: authData
    }
  }
  return createRequest(REQUEST_CONFIG)
}
```

### Store에서의 사용

보통 Store 형태를 취하는 방식에서 예시이다. 가독성과 사용성을 높이기 위해 async/await의 사용을 권장한다.

```javascript
// 위에서 정의한 user.api.js
import UserAPI from '@/api/user.api'

const actions = {
  // 비동기 방식으로 함수를 정의한다.
  async checkUserInfo({ state, commit }, e) {
    // import 한 UserAPI의 특정 함수를 호출한다. 필요시 파라미터를 전달한다.
    const result = await UserAPI.getUserInfo('userId')
    // 결과 받은 result를 콘솔로 확인한다.
    console.log(result)
    // 그리고 필요한 commit을 수행하여 데이터를 변경한다.
    commit('changeUserList', result)
  }
}
```
