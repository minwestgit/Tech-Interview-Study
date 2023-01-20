## Spring Webflux
우리가 보통 사용하던 Spring MVC + RDBMS 패턴은 Blocking IO 방식이다. 
Blocking IO 방식이라는 것은 요청을 처리하기 전까지는 다른 작업을 수행할 수 없는 상태라는 것을 말한다. 
동시에 여러 요청을 처리하기 위해서는 Thread 수를 늘려서 하는 방법이 존재하기는 하지만 이도 오버헤드가 발생한다. <br>
이를 개선하기 위해 나온 기술이 Non-Blocking IO 방식인 **Spring WebFlux**이다. **Spring WebFlux는 동시에 처리되어야 할 많은 요청에 대해 효율적으로 처리**해줄 수 있다. 
Spring WebFlux는 Spring 5에서 추가된 논블로킹(Non-Blocking) 런타임에서 리액티브 프로그래밍을 할 수 있는 새로운 Web 프레임워크이다.

- 장점 : 고성능, spring 과 완벽한 통합, netty 지원, 비동기 non-blocking 메세지 처리
- 단점 : 오류처리가 다소 복잡하다. Back Pressure 기능 없음


### Spring MVC vs Spring Webflux
![image](https://user-images.githubusercontent.com/70561950/213615281-75caa115-d5f0-46f2-83b7-4bd932112f8e.png)

Spring MVC와 WebFlux의 공통점은 @Controller, Reactive 클라이언트이다. 
둘 다 Tomcat, Jetty, Undertow와 같은 서버에서 실행할 수 있다. <br>
Spring MVC에서는 명령형 논리, JDBC, JPA를 가질 수 있다. 
Spring WebFlux에서는 기능적 엔드 포인트, 이벤트 루프, 동시성 모델을 가질 수 있습니다. Spring WebFlux는 Netty 서버에서 실행할 수 있다는 장점이 있다.
