## CORS

교차 출처 리소스 공유는 추가 HTTP 헤더를 사용하여, 한 출처에서 실행 중인 웹 어플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에게 알려주는 체제이다.

즉, 다른 출처에서 데이터를 주고받는 것을 허용하는 정책이다.

### 필요한 이유 → **SOP (Same Origin Policy)**

SOP(동일 출처 정책)란 웹 브라우저에서 보안을 강화하기 위하여 동일한 출처에서만 리소스를 주고 받도록 하는 정책이다. 동일 출처란 URL 중에서도 프로토콜, 도메인 주소, 포트 번호를 의미한다.

보안 상의 이유로, 브라우저들은 스크립트 내에서 초기화되는 cross-origin HTTP 요청을 제한한다. 하지만 웹 애플리케이션을 개선시키기 위해, 개발자들은 브라우저 벤더사들에게 XMLHttpRequest가 cross-domain 요청을 할 수 있도록 요청했고 이에 따라 CORS가 생겼다.

### 과정
- CORS 요청 시에는 미리 OPTIONS 주소로 서버가 CORS를 허용하는지 물어본다.
- 이때 Access-Control-Request-Method로 실제로 보내고자 하는 메서드를 알리고,
- Access-Control-Request-Headers로 실제로 보내고자 하는 헤더들을 알린다.
- Allow 항목들은 Request에 대응되는 것으로, 서버가 허용하는 메서드와 헤더를 응답하는데 사용된다.
- Request랑 Allow가 일치하면 CORS 요청이 이루어진다.

1. 단순 요청(Simple Request)<br>
Preflight 요청 없이 바로 요청을 보낸다.Simple Request는 아래와 같은 조건을 만족해야한다.

- 메서드 : GET, POST, HEAD
- Content-Type은 아래 셋 중 하나여야 한다.
    - application/x-www-form-urlencoded
    - multipart/form-data
    - text/plain
- 헤더 : Accept, Accept-Language, Content-Language, Content-Type 만 허용 한다.

2. 사전 요청 (Preflight Request)<br>
사전 요청은 OPTIONS 메서드를 통해 다른 도메인 리소스에 요청이 가능한지 확인하는 작업이다. 요청이 가능한 것을 확인하면 실제 요청을 보낸다. Access-Control-Request-Method에 HTTP 메서드, Access-Control-Request-Headers에 OPTIONS 메서드를 넣고 보낸다.

**Preflight Request**

- Origin : 요청 출처
- Access-Control-Request-Method : 실제 요청의 메서드
- Access-Control-Request-Headers : 실제 요청의 헤더

**Preflight Response**

- Access-Control-Allow-Origin : 해당 origin이 자원에 접근할 수 있도록 허용.
- Access-Control-Allow-Methods : 허용되는 메서드
- Access-Control-Allow-Headers : 허용되는 헤더
- Access-Control-Max-Age : Preflight 응답 캐싱 시간

여기서 **Preflight Response**의 응답 코드는 200대여야하고 Body는 비어있는 것이 좋다.

3. 인증 요청 (Credentialed Request)<br>
인증 관련 헤더를 포함할 때 사용하는 요청이다.

**클라이언트**

쿠키 또는 JWT 토큰을 담아 보낼 경우 credentials : include 를 포함하여 보낸다.

**서버**

Access-Control-Allow-Credentials : true 해야 클라이언트의 인증 포함 요청에 허용이 가능하다.

- 해결 방법
    - CORS는 브라우저가 사용하는 것이므로 서버→서버는 적용되지 않는다. 그러므로 프록시 서버를 추가로 만들어 사이에 두면 브라우저가 개입되지 않아 CORS 오류를 피할 수 있다.
    - 프론트 프록시 서버 설정
        - 프론트 서버에서 백엔드 서버로 요청을 보낼 때, 대상의 URL을 변경한다.
    - 직접 헤더 설정
        - 직접 헤더에 설정을 추가한다.
    - 스프링부트 설정
        - 설정 클래스를 만들고 `WebMvcConfigurer`을 구현하면 `addCorsMappings`란 메서드를 사용하여 CORS의 출처 및 설정 관리를 할 수 있다.
    
   <br>
   
#### Ref.
[https://velog.io/@frankle97/CORS란](https://velog.io/@frankle97/CORS%EB%9E%80)<br>
[https://valuefactory.tistory.com/1141](https://valuefactory.tistory.com/1141)<br>
[https://koras02.tistory.com/96](https://koras02.tistory.com/96)<br>
