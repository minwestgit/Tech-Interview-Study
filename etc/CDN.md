## CDN(Content Delivery Network)
CDN은 Content Delivery Network의 약자로서 지리적인 제약 없이 전 세계 사용자에게 빠르고 안전하게 컨텐츠 전송을 할 수 있는 기술을 말한다. 이를 통해서 컨텐츠의 병목현상을 피할 수 있다.
<br>
CDN(Content Delivery Network)은 물리적으로 떨어져 있는 사용자에게 컨텐츠를 더 빠르게 제공하기 위해 고안된 기술이다. 만약 우리나라에 있는 사람이 미국에 있는 서버로부터 이미지나 파일 등을 다운받으려고 한다면 시간이 오래 걸릴 것이다. **따라서 서버를 분산시켜 캐싱해두고 사용자의 컨텐츠 요청이 들어오면 사용자와 가장 가까운 위치에 존재하는 서버로 매핑시켜 요청된 콘텐츠의 캐싱된 내용을 내어주는 방식으로 빠르게 데이터를 전송할 수 있게 된다.** 만약 서버가 파일을 찾는데 실패하는 경우 CDN 플랫폼의 다른 서버에서 컨텐츠를 찾은다음 응답을 전송한다.

1. 최초 요청은 서버로부터 컨텐츠를 가져와 고객에게 전송하며 동시에 CDN 캐싱장비에 저장한다.
2. 최초 요청 이후로의 요청은 CDN 에서 지정하는 해당 컨텐츠 만료 시점까지 캐싱된 컨텐츠를 전송한다.
3. 자주 사용하는 페이지에 한해서 캐싱되며, 해당 컨텐츠 호출이 없을 경우 주기적으로 삭제된다.
4. 서버가 파일을 찾는데 실패하는 경우 CDN 플랫폼의 다른 서버에서 컨텐츠를 찾은다음 엔드유저에게 응답을 전송한다.
5. 컨텐츠를 사용할 수 없거나 오래된 경우 CDN은 향후 요청에 대해 응답할 수 있도록 새로운 컨텐츠를 저장한다.

![image](https://user-images.githubusercontent.com/70561950/209813211-9198dd6b-8f10-40c2-ba97-029fc018c795.png)
- 왼쪽 : CDN을 사용하지 않을 경우
- 오른쪽 : CDN을 사용할 경우

<br>

### 캐싱 방식

#### Static Caching

- Origin Server 에 있는 Content를 운영자가 미리 Cache Server에 복사 해두어 사용자가 Cache Server에 Content 요청 시 무조건 Cache Server에 있다
- 대부분의 국내 CDN에서 이 방식을 사용 (게임 클라이언트 다운로드 등)

#### Dynamic Caching

- Origin Server에 있는 Content를 운영자가 미리 Cache Server에 복사하지 않음
- 사용자가 Content를 요청 시 해당 Content가 없는 경우 Origin Server로부터 다운로드 받아 전달한다. 있는 경우에는 캐싱된 Content전달
- 각각의 Content는 일정 시간 이후 Cache Server에서 삭제 될 수도 있다.