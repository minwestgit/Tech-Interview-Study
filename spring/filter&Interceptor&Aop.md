## Filter & Interceptor & AOP
![](https://t1.daumcdn.net/cfile/tistory/9983FB455BB4E5D30C)

Filter와 Interceptor, AOP 셋 다 Controller 전에 처리된다.

### Filter
서블릿 필터는 DispatcherServlet(가장 앞단에서 HTTP 프로토콜로 들어오는 모든 요청을 가장 먼저 받아 적합한 컨트롤러에 위임해주는 프론트 컨트롤러) 이전에 실행이 되는데 필터가 동작하도록 지정된 자원의 앞 단에서 요청내용을 변경하거나, 여러가지 체크를 수행할 수 있다. 또한 자원의 처리가 끝난 후 응답내용에 대해서도 변경하는 처리를 할 수가 있다.
⇒ 전체적인 Request단에서 어떤 처리가 필요할때. 문자 인코딩 등
보통 web.xml에 등록하고, 일반적으로 인코딩 변환 처리, XSS방어 등의 요청에 대한 처리로 사용된다.
- init() - 필터 인스턴스 초기화
- doFilter() - 전/후 처리
- destroy() - 필터 인스턴스 종료

### Interceptor
인터셉터는 스프링의 DistpatcherServlet이 컨트롤러를 호출하기 전, 후로 끼어들기 때문에 스프링 컨텍스트(Context, 영역) 내부에서 Controller(Handler)에 관한 요청과 응답에 대해 처리한다.
⇒ 세션 및 쿠키 체크하는 http 프로토콜 단위로 처리해야 하는 업무가 있을 때. 로그인 세션 체크 등
스프링의 모든 빈 객체에 접근할 수 있다. 인터셉터는 여러 개를 사용할 수 있고 로그인 체크, 권한체크, 프로그램 실행시간 계산작업 로그확인 등의 업무처리에 사용된다.
Spring 레벨에서 지원하는 Servlet Filter 이다. Spring Context 레벨에서 동작하므로 Dispatcher Servlet 이 Request 및 Response 를 처리하는 시점에 Interceptor Handler 가 동작한다.
DispatcherServlet에서 Handler(Controller)로 가기전에 정보 처리
스프링의 DispatcherSevlet이 Controller를 호출하기 전, 후에 끼어들기 때문에 스프링 컨텍스트 내부에서 Controller에 관한 요청과 응답에 관여한다.
SpringFramework에서 자체적으로 제공하는 기능
- preHandler() - 컨트롤러 메서드가 실행되기 전
- postHanler() - 컨트롤러 메서드 실행직 후 view페이지 렌더링 되기 전
- afterCompletion() - view페이지가 렌더링 되고 난 후

![image](https://user-images.githubusercontent.com/70561950/178116043-6aec5ce6-03be-4591-96f8-62ef13aef5d1.png)

### AOP
AOP는 새로운 프로그래밍 패러다임이 아니라 OOP(Object Oriented Programming, 객체 지향 프로그래밍)를 돕는 보조적인 기술로, 핵심적인 관심 사항(Core Concern)과 공통 관심 사항(Cross-Cutting Concern)으로 분리시키고 각각을 모듈화 하는 것을 의미한다. 예를 들어 우리가 개발한 API중에 회원 가입 API가 있다면, 핵심적인 관심 사항은 회원가입이라는 비지니스 로직이 될 것이고, 공통 관심 사항은 호출 시간 측정 로직이 될 것이다.
애플리케이션에 공통적으로 나타나는 부가적인 기능들을 독립적으로 모듈화하는 프로그래밍 모델
객체 지향의 프로그래밍을 했을 때 중복을 줄일 수 없는 부분을 줄이기 위해 종단면(관점)에서 바라보고 처리한다.
주로 '로깅', '트랜잭션', '에러 처리'등 비즈니스단의 메서드에서 조금 더 세밀하게 조정하고 싶을 때 사용한다.
Interceptor나 Filter와는 달리 메소드 전후의 지점에 자유롭게 설정이 가능하다.
Interceptor와 Filter는 주소로 대상을 구분해서 걸러내야하는 반면, AOP는 주소, 파라미터, 애노테이션 등 다양한 방법으로 대상을 지정할 수 있다.
