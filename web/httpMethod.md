## HTTP 메서드

- GET : 리소스 조회. url 형식으로 query를 통해 서버에 데이터 전달(요청).

- POST : 데이터 요청 처리. http 메시지 바디를 통해 서버로 데이터 전달. 주로 신규 리소스를 등록하거나 프로세스 처리에 사용

- PUT : 리소스가 있으면 대체하고 없으면 생성함. 쉽게 말하자면 Update. 데이터를 덮어씌움.
(PUT은 POST와 다르게 클라이언트가 리소스의 위치를 알고 URI를 지정해 주어야 한다)

- PATCH : PUT과 마찬가지로 리소스를 수정할 때 사용하지만, 리소스 일부만 변경.

- DELETE : 리소스 삭제

#### 잘 사용되지 않는 메소드들
- HEAD : GET과 동일하지만 메시지 바디를 제외하고 반환
- OPTIONS : 대상 리소스에 대한 통신을 설정하는 데 사용
- CONNECT : 대상 자원으로 식별되는 서버에 대한 터널을 설정


## HTTP 상태코드
- 1xx (Informational) : 요청이 수신되어 처리중
- 2xx (Successful) : 요청 정상 처리
- 3xx (Redirection) : 요청을 완료하려면 추가 행동이 필요
- 4xx (Client Error) : 클라이언트 오류, 잘못된 문법등으로 서버가 요청을 수행할 수 없음
- 5xx (Server Error) : 서버 오류, 서버가 정상 요청을 처리하지 못함