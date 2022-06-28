## 서블릿
클라이언트의 요청을 처리하고, 그 결과를 반환하는 Servlet 클래스의 구현 규칙을 지킨 자바 웹 프로그래밍 기술
간단히 말해서, 서블릿이란 자바를 사용하여 웹을 만들기 위해 필요한 기술로 클라이언트 요청 처리해 응답 전송해주는 기술. MVC 패턴 에서 컨트롤러로 이용됨.
웹서버가 동적인 페이지를 제공할 수 있도록 도와주는 어플리케이션이 서블릿

### 동작 과정
1. 사용자(클라이언트)가 URL을 입력하면 HTTP Request가 Servlet Container로 전송합니다.
2. 요청을 전송받은 Servlet Container는 HttpServletRequest, HttpServletResponse 객체를 생성합니다.
3. web.xml을 기반으로 사용자가 요청한 URL이 어느 서블릿에 대한 요청인지 찾습니다.
4. 해당 서블릿에서 service메소드를 호출한 후 클리아언트의 GET, POST여부에 따라 doGet() 또는 doPost()를 호출합니다.
5. doGet() or doPost() 메소드는 동적 페이지를 생성한 후 HttpServletResponse객체에 응답을 보냅니다.
6. 응답이 끝나면 HttpServletRequest, HttpServletResponse 두 객체를 소멸시킵니다.

### 서블릿 컨테이너
서블릿을 관리해주는 컨테이너. 
클라이언트의 요청(Request)을 받아주고 응답(Response)할 수 있게, 웹서버와 소켓으로 통신하며 대표적인 예로 톰캣(Tomcat)이 있다. 톰캣은 실제로 웹 서버와 통신하여 JSP(자바 서버 페이지)와 Servlet이 작동하는 환경을 제공해준다.
