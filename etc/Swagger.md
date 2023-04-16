## Swagger

Swagger 는 REST API를 설계, 빌드, 문서화 및 사용, 관리할 수 있는 Opp Api Specification(OAS)를 위한 프레임워크. Springboot에서 Swagger를 사용하면, 컨트롤러에 명시된 어노테이션을 해석하여 API문서를 자동으로 만들어준다. 참고로 Swagger는 Java에 종속된 라이브러리가 아니다.

[http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html) 여기서 확인 가능

**기능 :** API 설계, API 빌드, API 문서화(시각화), API 테스팅, API 표준화
<br>

Config 설정

- `useDefaultResponseMessages()`
    - `false`로 설정하면 swagger에서 제공해주는 응답코드(200, 401, 405, 404) 에 대한 기본 메시지를 노출하지 않는다.
    - 불필요한 응답코드와 메시지를 제거하기 위함이며, 컨트롤러에서 따로 명시해준다.
- `select()`
    - `ApiSelectorBuilder`를 생성한다.
- `apis()`
    - -api 스펙이 작성되어 있는 패키지를 지정한다.
    - 컨트롤러가 존재하는 패키지를 `basepackage` 로 지정하여, RequestMapping(GetMapping, PostMapping…)이 선언된 API를 문서화 한다.
- `paths()`
    - `apis()`로 선택되어진 API 증 특정 path 조건에 맞는 APi들을 다시 필터링하여 문서화한다.
- `apiInfo()`
    - Swagger UI에 노출할 정보
    - 제목, 설명 등 문서에 대한 정보들을 보여주기 위해 호출한다.
    
    Controller 설정
    
- @Operation : API 동작에 대한 명세 작성.
    - summary : 간단 설명
    - description : 상세 설명
    - response : response 리스트 → @ApiResponse로 response들 설정. 상태코드, 설명 등
    - parameters: 파라미터 리스트
