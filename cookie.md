# cookie를 통한 JWT 사용

![인증 프로세스](https://user-images.githubusercontent.com/52027534/84860269-b91f0180-b0a9-11ea-9839-9e87d5cfe341.png)

## 인증 프로세스

- 최초 진입점을 통해 인증 토큰 A를 발급 받는다.
- A토큰을 들고 사용자 인증을 받아 B 토큰을 발급 받는다.
- B토큰은 시스템 내에서 매 요청마다 Header에 실어 보내 자동으로 인증받도록 한다.
- 인증과정에서 토큰이 만료되었으면 공통 핸들러에서 재 발급을 받거나 최초 인증과정으로 보내버린다.
- 토큰 만료시에 refresh 토큰을 활용한 재발급이 있지만, 복잡도가 매우 높아져서 보통 프로세스에선 도입하지 않는 걸 권장한다.

## 관련 항목 상세

### 토큰 저장  

토큰은 브라우저의 Storage, Cookie를 통해서 저장하는게 대표적이다.  
각 방식별로 장단점이 있으며, 상황에 맞게 사용해야 한다. 이 시나리오 에서는 쿠키에 저장하는것으로 가정한다. 
(오해의 소지가 있을 수 있는데, 쿠키를 사용해서 인증을 하는게 아니다. 단순히 토큰을 어디에 저장할지에 대해 이야기 하는 것.)
[관련 설명](http://lazyhoneyant.blogspot.com/2016/08/jwt.html)

- Storage(Local) : 브라우저의 로컬 스토리지에 저장한다. 접근이 편하고 제어가 쉽지만 XSS공격에 취약하다.
- Storage(Session) : 로컬과 비슷하게 동작하지만, 브라우저가 닫히면 사라진다.
- Cookies : CSRF공격에 취약하지만 스토리지 방식보다 보안을 위한 몇 가지 옵션이 더 존재한다.

### 토큰 A - 인증토큰(JWT)

사용자 인증을 위한 기본 토큰. 네트워크 내에나 특정 URL, 앱, 사용자 IP등을 토대로 시스템을 이용 가능한지에 대해 발급해준다.  
토큰 A는 특정 상태값을 가지고 있으며, 이 시나리오에서는 토큰을 쿠키로 생성해준다고 가정한다.
아래의 쿠키 특성들을 이용해서 좀 더 안전하게 사용하는것을 권장한다.

- httpOnly : 스크립트를 통해 접근할 수 없으며, 이 값은 request의 withCredential : true 옵션을 통해 자동으로 header에 전송 된다. 주의사항은 서버의 cors 정책이 * 인경우 보안 위배로 전송이 거부된다. cors 정책을 세울 수 없는 경우에는 httpOnly를 사용하면 안된다.
- secure : https를 통해서만 사용될 수 있도록 제한을 둔다
- domain : 해당 도메인을 통해서만 사용될 수 있도록 제한을 둔다
- API 호출시 withCredentials 옵션 예시
```javascript
const apiCall = axios.create({
  withCredentials: true,
  headers: {
    'Accept' : 'application/json',
    'Content-Type' : 'x-www-form-urlencoded'
  }
});
```

### 토큰 B - 사용자토큰(JWT)

토큰 A를 들고 사용자 인증을 받는데, 몇 가지 확인해야 될 사항이 있다.

- 토큰 A는 httpOnly 옵션, withCredentials를 통해request의 헤더에 자동으로 되게 하는편이 보안정책에 유리하다.
- 발급받은 토큰 B도 cookie에 저장한다.
- 토큰 B는 이제 인증 외의 모든 요청의 헤더에 Authorization: Bearer {token} 형식으로 자동으로 등록하도록 한다.
- 이미 스크립트 내에서 제어를 하는 값이고 JWT의 payload에 실려있는 값들을 클라이언트에서 활용하는경우가 많아 httpOnly 옵션은 사용하지 않는편이 좋다.
- Authorization 헤더 예시
```javascript
const userToken = 'userTokenSampler' // 이 부분에 jwt가 담긴다.
const apiCall = axios.create({
  headers: {
    'Accept' : 'application/json',
    'Content-Type' : 'x-www-form-urlencoded',
    'Authorization' : `Bearer ${userToken}`
  }
});
```

## 인증 실패

토큰 B를 통해 매 요청을 처리하는 도중 권한 오류가 발생하면 공통 핸들러를 통해 에러를 처리한다.   
3가지 시나리오를 통해 처리하는데, 하나는 refresh 토큰을 통한 재발급이 있으며,  
다른 하나는 인증 프로세스 최초지점으로 돌아가서 재 인증을 거치는 방식이다.  
마지막으로 사용자를 로그아웃 시키거나, 안내를 통해 시스템을 종료하게 하는 방법이다.

- refresh 토큰 : 사용자 토큰을 받을때 인증용 토큰과 인증용 토큰 재발급을 위한 refresh 토큰을 같이 받을 수 있다. refresh 토큰의 사용은 복잡한 시스템에서 사용자의 인증 정보를 유지시켜줘야 할때 유용한 방식이지만, 복잡성이 매우 높아지고, 토큰 탈취의 위험에 좀 더 노출되어 있다.
- 최초지점 이동 : 시스템 최초 진입시 항상 재인증을 받게 하는 경우에 유용하다. 토큰 A를 받는 최초 인증이나, B토큰 발급시 에러가 생길경우에 대한 시나리오를 충분히 대비해야 한다.
- 로그아웃 : 시스템이 아주 간편하며, 재진입에 부담이 없을때 사용하기 유용한 시나리오다.

## 정리하며

JWT를 사용하는 방식은 상태정보를 서버에서 관리하지 않기때문에 아주 편리하고 인증에 들어가는 비용이 줄어들지만, 브라우저에서의 관리는 늘어나는 경향이 있다.  
어딘가에 항상 저장해야 하고, 탈취의 위험이 있어서 기간의 만료나 인증 받는 방식등에 고민을 많이 해야 한다. 그 외 CORS에 대한 이해등 많은 제약조건등이 그것이다.  
SPA를 기본으로 사용하는 추세에 JWT는 선택이 아닌 필수처럼 여겨지는 만큼, 특성을 정확히 파악해야 보안 문제의 발생을 최소로 억제할 수 있다.

## 참고 내용

[JWT](https://jwt.io/)  
[JWT이해하기](http://www.opennaru.com/opennaru-blog/jwt-json-web-token/)  
[XSS를 이용한 JWT 탈취-local storage](https://medium.com/redteam/stealing-jwts-in-localstorage-via-xss-6048d91378a0)  
[CSRF를 이용한 JWT 탈취-cookie](https://medium.com/@mena.meseha/how-to-defend-against-csrf-using-jwt-8adebe64824b)  
[withCredentials 과 CORS * 의 상관관계](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/Errors/CORSNotSupportingCredentials)  
[OAuth](https://oauth.net/2/)  
[OAuth이해하기](https://d2.naver.com/helloworld/24942)  
