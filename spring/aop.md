## AOP
<img width="717" alt="스크린샷 2022-08-22 오후 11 55 53" src="https://user-images.githubusercontent.com/70561950/185952337-142f4c16-4649-48b3-b48e-c86e78ec678f.png">

### 용어 정리
**조인포인트(Join Point)**
- 어드바이스(부가기능)가 적용될 수 있는 위치를 말한다.
- 조인 포인트는 추상적인 개념이다. AOP를 적용할 수 있는 모든 지점이라고 생각하면 된다.
- 타겟 객체가 구현한 인터페이스의 모든 메서드는 조인 포인트가 된다.
- 스프링 AOP는 프록시 방식을 사용하므로 조인 포인트는 항상 메소드 실행 지점으로 제한된다.

**타겟(Target)**
- 핵심 기능을 담고 있는 모듈로 타겟은 부가기능을 부여할 대상이 된다.

**포인트 컷(Pointcut)**
- 어드바이스를 적용할 타겟의 메서드를 선별하는 정규표현식이다.
- 조인 포인트 중에서 Advice가 적용될 위치를 선별하는 기능이다.
- 프록시를 사용하는 스프링 AOP는 메소드 실행 지점만 포인트컷으로 선별 가능

**어드바이스(Advice)**
- 어드바이스는 타겟에 제공할 부가기능을 담고 있는 모듈이다.
- Aspect를 언제 핵심 코드에 적용할 지를 정의한다. (특정 조인 포인트에서 Aspect에 의해 취해지는 조치)
- Around(주변), Before(전), After(후)와 같은 다양한 종류의 Advice가 있다.

**애스펙트(Aspect)**
- 애스펙트는 AOP의 기본 모듈이다.
- 애스펙트 = 어드바이스 + 포인트컷 (Advice + Pointcut을 모듈화 한 것)
- 여러 객체에 공통으로 적용되는 기능을 말한다. (공통 기능)
- 애스펙트는 싱글톤 형태의 객체로 존재한다.

**어드바이저(Advisor)**
- 하나의 Advice와 하나의 Pointcut으로 구성
- 어드바이저는 Spring AOP에서만 사용되는 특별한 용어이다.

**위빙(Weaving)**
- 위빙은 포인트컷에 의해서 결정된 타겟의 조인 포인트에 어드바이스를 적용하는 과정을 뜻한다.
- 위빙은 AOP가 핵심기능(타겟)의 코드에 영향을 주지 않으면서 필요한 부가기능(어드바이스)를 추가할 수 있도록해주는 핵심적인 처리과정이다.

<br>

### Spring AOP의 구현 방식
1. XML 기반의 POJO 클래스를 이용한 AOP 구현
- 부가기능을 제공하는 Advice 클래스를 작성한다.
- XML 설정 파일에 <aop:config>를 이용해서 애스펙트를 설정한다.
(즉, 어드바이스와 포인트컷을 설정함)

2. @Aspect 어노테이션을 이용한 AOP 구현
- @Aspect 어노테이션을 이용해서 부가기능을 제공하는 Aspect 클래스를 작성한다.
- 이 때 Aspect 클래스는 어드바이스를 구현하는 메서드와 포인트컷을 포함한다.
- XML 설정 파일에 <aop:aspectj-autoproxy />를 설정한다.


<br>

#### Ref.
[https://shlee0882.tistory.com/206](https://shlee0882.tistory.com/206)
[https://velog.io/@hyun6ik/AOP-용어-정리](https://velog.io/@hyun6ik/AOP-%EC%9A%A9%EC%96%B4-%EC%A0%95%EB%A6%AC)
[https://yeoncoding.tistory.com/175](https://yeoncoding.tistory.com/175)
