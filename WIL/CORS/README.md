
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
>
1.Origin : 요청 출처<br>
2.Access-Control-Request-Method : 실제 요청의 메서드<br>
3.Access-Control-Request-Headers : 실제 요청의 추가 헤더<br>

> **__Preflight Response__**
1.Access-Control-Allow-Origin : 허가 출처 <br>
2.Access-Control-Allow-Methods : 허가 메서드 <br>
3.Access-Control-Allow-Headers : 허가 헤더 <br>
4.Access-Control-Max-Age : Preflight 응답 캐시 시간 <br>
여기서 Preflight Response의 응답 코드는 200대여야하고 Body는 비어있는 것이 좋다.<br>

-----
> ❗️**__인증 요청(Credentialed Request)__** <br>
> 인증 관련 헤더를 포함할 때 사용하는 요청이다.
> 1. 클라이언트 : 쿠키 또는 JWT 토큰을 담아 보낼 경우 credentials : include 를 포함하여 보낸다.
> 2. 서버 : ccess-Control-Allow-Credentials : true 해야 클라이언트의 인증 포함 요청에 허용이 가능하다.

-----

> ❗️ **__CORS__** <br>
> CORS 해결 방법에는 세 가지가 있다.
> 

- 모델2 방식은 View Model Controller 가 각각 구분되어 있는 모델이다. HTML 소스와 Java 소스를 분리시켜놓았기때문에 모델1 방식에 비해 확장시키고 유지보수하기 쉽다.ㅂㅏㅇ법에는
- 모델2 방식은 View Model Controller 가 각각 구분되어 있는 모델이다. HTML 소스와 Java 소스를 분리시켜놓았기때문에 모델1 방식에 비해 확장시키고 유지보수하기 쉽다.
