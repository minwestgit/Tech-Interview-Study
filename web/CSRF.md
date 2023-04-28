# CSRF(Cross Site Request Forgery, XSRF)

사이트 간 요청 위조이라는 뜻으로,  웹사이트 취약점 공격의 하나다. 사용자가 자신의 의지와는 무관하게 공격자가 의도한 행위(수정, 삭제, 등록 등)를 특정 웹사이트에 요청하게 하는 공격을 말한다. 공격자가 클라이언트의 권한을 도용하여 특정 웹 사이트의 기능을 실행하게 할 수 있다.

- 특정 웹사이트가 사용자의 웹 브라우저를 신용하는 상태를 노린 공격 방식이다.
- 사용자가 웹사이트에 **로그인한 상태**에서 사이트간 **요청 위조 공격 코드가 삽입된 페이지**를 열면, 공격 대상이 되는 웹사이트는 위조된 공격 명령이 믿을 수 있는 사용자로부터 발송된 것으로 판단하게 되어 공격에 노출된다.

ex) 해커가 사용자의 권한을 도용하여 광고성 글을 올린다.

### 공격 과정

1. 이용자는 웹사이트에 로그인하여 정상적인 쿠키를 발급받는다.

2. 공격자는 특정 링크를 이메일이나 게시판 등의 경로를 이용자에게 전달한다.

ex) [http://www.geocities.com/attacker](http://www.geocities.com/attacker)

3. 공격용 HTML 페이지는 다음과 같은 이미지태그를 갖는다.

`<img src= "https://travel.service.com/travel_update?.src=Korea&.dst=Hell">`

- 해당 링크는 클릭시 정상적인 경우 출발지와 도착지를 등록하기위한 링크다. 위의 경우 도착지를 변조하였다.

4. 이용자가 공격용 페이지를 열면, 브라우저는 이미지 파일을 받아오기 위해 공격용 URL을 연다.

5. 이용자의 승인이나 인지 없이 출발지와 도착지가 등록됨으로써 공격이 완료된다. 해당 서비스 페이지는 등록 과정에 대해 단순히 쿠키를 통한 본인확인 밖에 하지 않으므로 공격자가 정상적인 이용자의 수정이 가능하게 된다.


### 방어 방법

1. Referrer 검증

- Back-end에서 request의 referrer를 확인하여 도메인 (ex. *.tistory.com)이 일치하는 지 검증하는 방법이다. 같은 도메인에서 온 요청인지 검증하여 차단.
- 같은 도메인 내의 페이지에 XSS 취약점이 있는 경우 CSRF 공격에 취약해질 수 있다. 이때, 도메인 단위 검증에서 좀 더 세밀하게 페이지 단위까지 일치하는지 검증하면, 도메인 내의 타 페이지에서의 XSS 취약점에 의한 CSRF 공격을 방어할 수 있다.
    - (Http)referrer: 웹브라우저로 서핑할 때, 하이퍼링크를 통해 각각의 사이트로 방문시 남는 흔적을 말한다. 사이트 방문객이 어떤 경로로 자신의 사이트를 방문했는지 알아볼 때 유용하다.
    - XSS(cross-site scripting): 사이트간 스크립팅: 웹사이트 관리자가 아닌 이가 웹페이지에 악성 스크립트를 삽입할 수 있는 취약점

2. Security Token (CSRF Token)

- 사용자의 세션에 임의의 값을 저장하고 사용자의 요청 마다 해당 값을 전송시킨 후, Back-end에서 요청을 받을 때마다 세션에 저장된 토큰 값과 파라미터에 전달되는 토큰 값이 일치하는 지 검증하는 방법이다.
- Referrer 검증이 불가한 환경에서 사용할 수 있다.
- 이 방법 또한 같은 도메인 내에 XSS 취약점이 있다면, CSRF 공격에 취약해진다.

3. CAPCHA 사용
이미지를 보여주고 그 이미지에 해당하는 문자/숫자/그림이 아니라면 요청을 거부
하기 때문에 CSRF 공격을 효과적으로 방어할 수 있는 방법이다.


<br>

#### Ref.
[https://scshim.tistory.com/527](https://scshim.tistory.com/527) <br>
[https://crossjin.tistory.com/entry/CSRFCross-Site-Request-Forgery란](https://crossjin.tistory.com/entry/CSRFCross-Site-Request-Forgery%EB%9E%80)<br>
[https://tibetsandfox.tistory.com/11](https://tibetsandfox.tistory.com/11)
