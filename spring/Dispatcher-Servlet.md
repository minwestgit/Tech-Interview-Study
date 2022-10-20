## Dispatcher-Servlet 과정

![image](https://user-images.githubusercontent.com/70561950/196662148-4dd1e911-1ee6-4697-8b6f-0cc1959f14ca.png)

1. 클라이언트의 요청을 디스패처 서블릿이 받음
디스패처 서블릿은 가장 먼저 요청을 받는 프론트 컨트롤러입니다. 서블릿 컨텍스트(웹 컨텍스트)에서 필터들을 지나 스프링 컨텍스트에서 디스패처 서블릿이 가장 먼저 요청을 받게됩니다.
2. 요청 정보를 통해 요청을 위임할 컨트롤러를 찾음
디스패처 서블릿은 컨트롤러에게 요청을 위임해야 하는데 그러기 위해서는 요청을 위임할 컨트롤러를 찾아야 합니다. HandlerMapping의 구현체 중 하나인 RequestMappingHandlerMapping은 모든 컨트롤러 빈을 파싱하여 HashMap으로 (요청 정보, 요청을 처리할 대상)을 관리합니다. 위에서는 쉬운 이해를 위해 컨트롤러라고 했지만 엄밀히 말해서는 요청에 매핑되는 컨트롤러, 메소드 등을 갖는 HandlerMethod 객체입니다.
그래서 HadlerMapping은 요청이 오면 Http Method, URI 등을 사용해 요청 정보를 객체로 만들고, Map의 Key로 사용해 요청을 처리할 HandlerMethod를 찾고 HandlerMethodExecutionChain으로 감싸서 반환합니다. HandlerMethodExecutionChain으로 감싸는 이유는 컨트롤러로 요청을 넘겨주기 전에 처리해야 하는 인터셉터 등을 포함하기 위해서입니다.
3. 요청을 컨트롤러로 위임할 핸들러 어댑터를 찾아서 전달함
디스패처 서블릿은 컨트롤러로 요청을 직접 위임하는 것이 아니라 HandlerAdapter를 통해 컨트롤러로 요청을 위임합니다. 이때 Adapter를 통해 컨트롤러를 호출하는 이유는 공통적인 전/후처리 과정이 필요하기 때문입니다. 대표적으로 요청 시에 @RequestParam, @RequestBody 등을 처리하기 위한 ArgumentResolver들과 응답 시에 ResponseEntity의 Body를 Json으로 직렬화하는 ReturnValueHandler들이 어댑터를 통해 처리됩니다.
그래서 디스패처 서블릿은 대신 컨트롤러로 요청을 위임할 HandlerAdapter 구현체인 RequestMappingHandlerAdapter를 찾습니다. 그리고 앞서 찾은 HandlerMethodExecutionChain이 갖는 인터셉터들을 모두 실행한 다음에 HandlerAdapter를 통해 컨트롤러의 메소드를 호출하도록 요청을 위임합니다.
4. 핸들러 어댑터가 컨트롤러로 요청을 위임함
요청을 처리할 대상 정보인 HandlerMethod 객체에는 컨트롤러 정보와 메소드 객체가 있으므로 리플렉션의 메소드 객체를 invoke 합니다. 사실 엄밀히 말해서는 HandlerMethod에 컨트롤러 빈 이름과 메소드, 빈 팩토리가 있어서 빈 팩토리에서 컨트롤러 빈을 찾는 등의 작업이 일어나는데 그렇게 중요하지는 않습니다.
5. 비지니스 로직을 처리함
6. 컨트롤러가 반환값을 반환함
ResponseEntity 또는 View 이름 등
7. HandlerAdapter가 반환값을 처리함
컨트롤러로 요청을 위임한 HandlerAdapter는 컨트롤러로부터 받은 응답을 ReturnValueHandler를 통해 후처리한 후에 디스패처 서블릿으로 돌려줍니다. 만약 컨트롤러가 ResponseEntity를 반환하면 HttpEntityMethodProcessor가 MessageConverter를 사용해 응답 객체를 직렬화(객체→json)하고 응답 상태(HttpStatus)를 설정합니다. 만약 컨트롤러가 View 이름을 반환하면 ViewResolver를 통해 View를 반환하게 됩니다.
8. 서버의 응답을 클라이언트로 반환함
디스패처 서블릿을 통해 반환되는 응답은 다시 필터들을 거쳐 클라이언트에게 반환됩니다.

[https://mangkyu.tistory.com/180?category=761302](https://mangkyu.tistory.com/180?category=761302)
