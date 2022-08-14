
# WIL - CORS
- 2022.08.14

## ❓ [SOP(Same Origin Policy)]
- 📌 SOP 이란? <br>
- CORS를 알기 이전에, SOP에 대해 알아보자.<br>
- SOP는 다른 출처의 리소스를 사용하는 것을 제한하는 보안 방식이다.<br>
- 여기서 출처는 URL의 Protocol, Host, Port 로 구분한다.<br>
- 토큰만으로 사용자를 판단한다면.. 클라이언트와 해커의 요청을 구분하기 힘들것이다.<br>
- 반면에 URL을 확인한다면 클라이언트의 출처와 해커의 출처가 서로 다른 출처라는 것을 확인하여, 악의적인 요청을 방지할 수 있다.<br>
- 위와 같은 상황, 요청의 출처가 다르다면 Cross Origin SOP에 위반이라고 한다.<br>
- 하지만 외부 라이브러리도 사용해야 하는데 요청과 리소스를 매번 동일한 출처로만 받을 수는 없다.<br>
- 이 떄 필요한 것이 CORS 이다.
-----

## ❓ [CORS(Corss Origin Resource Sharing)]
- 📌 CORS 란? <br>
- CORS란 다른 출처의 자원을 공유하는 것이다.<br>
> 교차 출처 리소스 공유는 추가 HTTP 헤더를 사용하여, 한 출처에서 실행 중인 웹 어플리케이션이<br>
> 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에게 알려주는 체제이다.<br>
- CORS 접근제어에 사용되는 3가지의 시나리오가 있다.<br>
-----
> ❗️**__단순 요청(Simple Request)__** <br>
> Preflight 요청 없이 바로 요청을 보낸다. Simple Request는 아래와 같은 조건을 만족해야한다. <br>
> **__메서드 : GET, POST, HEAD__** <br>
**__Content-Type은 아래 셋 중 하나여야 한다.__**<br>
application/x-www-form-urlencoded <br>
multipart/form-data <br>
text/plain <br>
**__헤더 : Accept, Accept-Language, Content-Language, Content-Type 만 허용 한다.__** <br>
-----
> ❗️**__사전 요청(Preflight Request)__** <br>
> 사전 요청은 OPTIONS 메서드를 통해 다른 도메인 리소스에 요청이 가능한지 확인하는 작업이다. <br>
> 요청이 가능한 것을 확인하면 실제 요청을 보낸다.<br>
> **__Preflight Request__**<br>
> Origin : 요청 출처<br>
Access-Control-Request-Method : 실제 요청의 메서드<br>
Access-Control-Request-Headers : 실제 요청의 추가 헤더<br>
-----


> ❗️ ORM 사용 이유 <br>
> **__1. 객체 지향 프로그래밍은 클래스를 이용하고 관계형 데이터베이스는 테이블을 이용하는데 객체 모델과 관계형 모델 간의 불일치가 존재한다.__**<br>
> **__2. ORM을 이용해서 데이터베이스 접근을 프로그래밍 언어의 관점에서 맞출 수 있다.__**<br>
> **__3. ORM을 이용해서 객체 간의 관계를 바탕으로 SQL을 자동으로 생성하여 불일치를 해결한다.__**<br>
> **__4. ORM을 이용해서 객체를 통해 간접적으로 데이터베이스를 다룬다.__**<br>
> **__5. 이를 통해 데이터베이스 세계와 프로그래밍 언어 사이의 개념의 간극을 줄여준다.__**<br>
> **__6. 이를 통해 느슨하게 연결된, 테스트에 용이한 어플리케이션을 만들 수 있다.__**<br>
------
-----
> ❗️ ORM 장점 <br>
> **__1. 직관적인 코드(가독성) + 비지니스 로직 집중 가능(생산성)__**<br>
> **__2. 재사용 및 유지보수 편리성 증가__**<br>
> **__3. DBMS에 대한 종속성 저하__**<br>
------
-----
> ❗️ ORM 단점 <br>
> **__1. 사용하기는 편리하지만 설계는 신중하게 해야한다.__**<br>
> **__2. 프로젝트의 복잡성이 커질 경우 난이도 또한 올라간다.__**<br>
> **__3. 잘못 구현된 경우 일관성이 무너지는 문제점이 생길 수 있다.__**<br>
------


## ❓ [SQL (Structured Query Language, 구조적 질의 언어)] 
- 📌 SQL은 관계형 데이터베이스 시스템(RDBMS)을 제어하는 컴퓨터 언어이다.<br>
- 일반적인 프로그래밍 언어(범용 언어)와 달리 대화식 언어이기 때문에, 명령문이 짧고 간결하다.<br>
- SQL 자체는 범용 언어에 비해 한계가 있기 때문에, 단독으로 사용하기 보단 다른 고수준 언어와 함께 쓰는 것이 일반적이다.<br>
-----
> ❗️SQL 쿼리 문의 분류 <br>
> **__1. DDL (Data Definition Language, 데이터 정의어) / 오브젝트를 생성,삭제,변경하는 역할 (CREATE, DROP, ALTER)__**<br>
> **__2. DML (Data Maipulation Language, 데이터 조작어) / DB를 조회,삽입,삭제,변경하는 역할 (SELECT, INSERT, UPDATE...)__**<br> 
> **__3. DCL (Data Control Language, 데이터 제어어) / 사용자의 권한을 관리하는 역할 (GRANT, DENY, REVOKE)__**<br>
> **__일반적인 언어의 중요도는 DML > DDL > DCL 순입니다.__**
-----


## ❓ [MVC (Model - View - Controller)]
- 📌 MVC란 어플리케이션의 역할을 Model - View - Controller 세 가지 역할로 구분한 개발 방법론이다.<br>
- MVC 패턴을 성공적으로 사용하면, 사용자 인터페이스로부터 비지니스 로직을 분리하여 어플리케이션의 시각적 요소나 그 이면에서 실행되는 비지니스 로직을 서로 영향 없이 쉽게 고칠 수 있다.<br>
- MVC 패턴은 모델1 방식과 모델2 방식이 있는데, 모델1 방식은 Controller 영역에 View 영역을 같이 구현하는 방식이다.<br>
- 모델2 방식은 View Model Controller 가 각각 구분되어 있는 모델이다. HTML 소스와 Java 소스를 분리시켜놓았기때문에 모델1 방식에 비해 확장시키고 유지보수하기 쉽다.
-----
MVC 패턴 및 간단한 설명<br>
[개인블로그](https://rio0205.tistory.com/7)
-----
