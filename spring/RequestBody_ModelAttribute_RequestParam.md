## @RequestBody, @ModelAttribute, @RequestParam의 차이

### RequetParam
- 1개의 HTTP 파라미터를 얻기 위해 사용되며 기본값을 지정할 수 있음
- 필수 여부가 true이기 때문에 반드시 필요한 경우가 아니라면 required=false 설정이 필요함
- 
### RequestBody
- Json(application/json) 형태의 HTTP Body 데이터를 MessageConverter를 통해 Java 객체로 변환시킴
- 기본 생성자로 객체를 만들고, Getter나 Setter 등의 메소드로 필드를 찾아 Reflection으로 값을 설정함
- 
### ModelAttribute
- 폼 형태(form)의 HTTP Body와 요청 파라미터들을 객체에 바인딩시킴
- 기본적으로 생성자로 값이 설정되고, 생성자로 설정되지 않은 필드는 Setter로 설정됨

<br>

참고)
스프링은 String, int와 같은 단순 타입은 `@RequestParam`으로 보고, 그 외의 복잡한 오브젝트는 모두 `@ModelAttribute`가 생략된 것으로 간주한다. <br>
하지만 스프링은 간단한 숫자나 문자로 전달된 요청 파라미터를 복잡한 오브젝트로 변환할 수 있기 때문에 단순 타입이 아니라고 해서 꼭 `@ModelAttribute`가 생략됐다고 볼 수 없다. 
그래서 `@RequestParam`, `@ModelAttribute`을 작성해주는 것을 권장한다. 매우 단순한 커맨드 오브젝트나 파라미터라면 생략해도 나쁘진 않다.


Ref.
[https://mangkyu.tistory.com/72](https://mangkyu.tistory.com/72)
