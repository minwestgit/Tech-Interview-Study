## @Requestmapping 어노테이션 동작 방법
SpringBoot 어플리케이션이 실행되면 어플리케이션에서 사용할 bean들을 담을 ApplicationContext를 생성하고 초기화한다. requestMapping 어노테이션을 붙인 메서드들이 handler에 등록되는 것은 ApplicationContext가 초기화되는 과정에서 일어난다. 등록되는 Bean 중 하나가`RequestMappingHandlerMapping`이고, 이 빈이 우리가`@RequestMapping`
으로 등록한 메서드들을 가지고 있다가 요청이 들어오면 매핑해주는 역할을 수행한다.

1. 디스패처 서블릿이 앞에서 HTTP 요청을 먼저 받는다.
2. 디스패처 서블릿이 RequestMappingHandlerMapping를 통해 저장된 HandlerMethod 중에서 해당 요청에 매핑되는 HandlerMethod를 반환한다.
3. 디스패처 서블릿이 핸들러 어댑터(Handler Adapter)를 통해 HandlerMethod의 정보를 이용해 요청에 매핑되는 메소드를 실행한다.
