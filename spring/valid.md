## **@Valid와 @Validated 유효성 검증 차이**

### @Valid
- JSR-303 자바 표준 스펙
- 특정 ArgumentResolver를 통해 진행되어 컨트롤러 메소드의 유효성 검증만 가능하다.
- 유효성 검증에 실패할 경우 MethodArgumentNotValidException이 발생한다.
- 
### @Validated
- 자바 표준 스펙이 아닌 스프링 프레임워크가 제공하는 기능
- AOP를 기반으로 스프링 빈의 유효성 검증을 위해 사용되며 클래스에는 @Validated를, 메소드에는 @Valid를 붙여주어야 한다.
- 유효성 검증에 실패할 경우 ConstraintViolationException이 발생한다.
