# Javascript Advanced

<table>
    <thead>
        <th>구분</th>
        <th>내용</th>
    </thead>
    <tbody>
        <tr>
            <td>요약</td>
            <td>자바스크립트 상급자 가이드</td>
        </tr>
        <tr>
            <td>목표</td>
            <td>자바스크립트의 역량 향상</td>
        </tr>
        <tr>
            <td>기대효과</td>
            <td>자바스크립트 구조 및 모듈에 대한 이해, 제작 가능</td>
        </tr>
    </tbody>
</table>

## 목차

- [솔리드 원칙](<#솔리드 원칙>)
- [자료구조](#자료구조)
- [네트워크 및 통신 규약](#네트워크-및-통신-규약)
- [커스텀 이벤트](#커스텀-이벤트)
- [패턴](#패턴)

## 솔리드 원칙

객체 지향 프로그래밍(OOP : Object Oriented Programming) 및 설계의 다섯 가지 기본 원칙을 두문자어 기억술로 소개한 것을 SOLID 원칙이라고 합니다.

> S - 단일책임의 원칙 (SRP: Single Responsibility Principle)  
> O - 개방폐쇄의 원칙 (OCP: Open Close Principle)  
> L - 리스코브 치환의 원칙 (LSP: The Liskov Substitution Principle)  
> I - 인터페이스 분리의 원칙 (ISP: Interface Segregation Principle)  
> D - 의존성역전의 원칙 (DIP: Dependency Inversion Principle)

우리는 일을 하면서 수많은 코드와 마주하게 됩니다.  
시간이 지나도 유지 보수와 확장이 쉬운 시스템을 만들고자 하는 노력은 매우 중요합니다.  
프로그래머들은 가독성있고, 확장성 있는 코드를 만들기위해 고군분투 합니다.  
여기에 확장성있고 가독성이 있는 코드를 만드는 5가지 원칙에 대해 배웁니다.

### 참고자료

- [SOLID-1](http://www.nextree.co.kr/p6960/)
- [SOLID-2](https://medium.com/@cramirez92/s-o-l-i-d-the-first-5-priciples-of-object-oriented-design-with-javascript-790f6ac9b9fa)

## 자료구조

어떤 데이터의 구체적인 구현 방식은 생략한 채, 데이터의 추상적 형태와 그 데이터를 다루는 방법만을 정해놓은 것을 가지고 ADT(Abstract Data Type) 혹은 추상 자료형이라고 합니다.

> Queue - 순서대로 처리해야 하는 작업을 임시로 저장해두는 용도로 사용  
> Stack - 서로 관계가 있는 여러 작업을 연달아 수행하면서 이전의 작업 내용을 저장 할 때 사용  
> Tree - 여러 데이터가 계층 구조 안에서 서로 연결된 형태를 나타낼 때 사용

널리 사용되는 ADT인 큐, 스택, 트리에 대해 배웁니다.

### 참고자료

- [Data Structure (queue, stack, tree)](https://helloworldjavascript.net/pages/282-data-structures.html)

## 네트워크 및 통신 규약

인터넷은 IP(인터넷 규약) 기반으로 이루어져 있습니다.  
이 IP 위에서 우리는 데이터를 주고 받습니다.  
데이터를 전송함에 있어 따라야 하는 규약이 있는데, 이것을 TCP(전송 제어 규약)이라고 합니다.  
그리고 그 위에서 우리는 웹 어플리케이션들을 만들어 내죠.  
웹어플리케이션에 사용되는 규약은 HTTP, FTP 등이 있습니다. 우리는 주로 HTTP를 사용하죠.  
HTTP 프로토콜의 표준을 최대한 활용하여 여러 추가적인 장점을 함께 가져갈 수 있게 해준 REST API 까지,
인터넷 내의 여러 규약에 대해 배웁니다.

### 참고자료

- [TCP/IP](https://brunch.co.kr/@wangho/6)
- [HTTP](https://gmlwjd9405.github.io/2019/04/17/what-is-http-protocol.html)
- [REST](https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html)

## 커스텀 이벤트

함수간, 모듈간 결합도를 느슨하게 하기 위해서 사용되는 기법중 하나가 이벤트 주도 개발방법이 있습니다.  
이번에는 이벤트를 스스로 만들고 사용해 보는 법을 배웁니다.

### 참고자료

- [Custom Event](https://developer.mozilla.org/ko/docs/Web/Guide/Events/Creating_and_triggering_events)

## 패턴

자바스크립트의 패턴은 정말 다양합니다.  
자바스크립트가 함수형의 특징과 객체지향의 특징을 모두가지는 prototype 기반의 언어이기 때문입니다.  
그렇기 때문에 매우 유연하게 각 프로그래밍 개발 방법론적인 것을 흉내낼 수 있습니다.  
패턴에는 정답이 없습니다. 프로젝트에 가장 적합한 패턴을 찾고 응용하는것이 중요합니다.  
많이 사용되는 패턴에 대해 배웁니다.

### 참고자료

- [Memoization](https://github.com/FEDevelopers/tech.description/wiki/%EC%84%B1%EB%8A%A5-%ED%96%A5%EC%83%81%EC%9D%84-%EC%9C%84%ED%95%9C-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%A9%94%EB%AA%A8%EC%9D%B4%EC%A0%9C%EC%9D%B4%EC%85%98-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0)
- [Singleton](https://www.zerocho.com/category/JavaScript/post/57541bef7dfff917002c4e86)
- [Factory](https://velog.io/@godori/factory-method-pattern)
- [Prototype](https://jsdev.kr/t/javascript-prototype-pattern/2920)
- [Pipeline](https://medium.com/@danielkagan/how-to-write-your-own-pipe-function-in-js-da7d1a3e2a2a)

## 자바스크립트를 더 많이 알아보기(권장)

좋은 자바스크립트 개발자가 되기 위해 알아야 할 내용들이 더 있습니다.  
몰라도 개발은 할 수 있지만, 잘 하기 위해서는 알아야 할 내용들이라고 생각합니다.

- [33가지 자바스크립트 컨셉](https://github.com/leonardomso/33-js-concepts)
- [33가지 자바스크립트 컨셉-한글화](https://github.com/Lee-hyuna/33-js-concepts-kr/wiki)
- [현대 자바스크립트 자습서](https://javascript.info/)
- [다양한 자바스크립트 설계 패턴](https://www.dofactory.com/javascript/design-patterns)
