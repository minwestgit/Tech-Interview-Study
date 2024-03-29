## OAuth 2.0란?
사용자가 비밀번호를 노출하지 않고 다른 웹 사이트의 자신의 정보를 웹이나 애플리케이션에 접근 권한을 부여할 수 있는 개방형 표준 프로토콜.
- 인증 : 접근 자격이 있는지 검증
- 인가 : 자원에 접근할 권한을 부여

### 참여자
- Resource Server : 자원을 보유하고 있는 서버. Google, Kakao 등
- Resource Owner : 자원의 소유자. 로그인 하는 유저.
- Client : Server에 접속해 정보를 가져오고자 하는 클라이언트. 웹앱
- Authorization Server : 권한 서버. 인증/인가를 수행하는 서버로 클라이언트의 접근 자격을 확인하고 Access Token 발급하여 권한을 부여함.

### Token
- Access Token : 리소스 서버에서 리소스 오너의 자원을 획득할 때 사용되는 만료 기간이 있는 Key
- Refresh Token : Access Token 만료시 갱신하기 위한 용도로 사용하는 토큰.

### 과정
![image](https://user-images.githubusercontent.com/70561950/185392615-e3315edd-dcfc-404d-b75c-c484d53aa5fb.png)

** 클라이언트가 사전에 리소스 서버에 인증 정보 생성해야함.
1. 사용자가 내가 만든 웹사이트에서 어떤 웹페이지에 접근하려고 요청한다.
2. 내 사이트에서는 인증이 되지 않은 사용자의 요청(request)을 받으면 "구글한테 인증받고 올래?" 하고 동의를 구하는 페이지를 띄운다.
3. 사용자가 동의를 누르면 구글로 인증 요청이 가게된다.
4. 구글에서는 로그인이 안되어있으면 로그인을 할 수 있는 화면을 보여주고, 로그인이 되어있으면 "내가 만든 웹사이트에서 너의 구글계정에 있는 어떤 정보(API정보)를 가져다 쓴다는데 동의할거야?" 라고 구글이 동의를 구하는 화면을 보여준다.
5. 사용자가 동의하면 구글은 바로 정보를 주지 않고 인증 코드를 웹사이트에 준다.
6. 인증코드를 받은 웹사이트에서는 기존에 웹서비스를 구글에 등록하면서 받은 client id(ID)와 client secret(PW), 그리고 인증코드를 보낸다. (총 3개의 정보) → 권한 서버에
7. 그러면 구글이 올바른 클라이언트(웹사이트)의 요청이었음을 검증했기 때문에 access token을 준다.
8. 이제 사용자의 요청에 따라 구글 계정의 정보(API)가 필요하면 구글에 access token을 내밀면서 정보를 받아다가 쓸 수 있다.


<br>

#### Ref.
https://kingpiggylab.tistory.com/323
https://developers.payco.com/guide/development/start
