# spring Security

## Spring Security?
- 애플리케이션의 보안(인증과 권한, 인가 등)을 담당하는 스프링 하위 프레임워크
- **'인증'과 '권환'**에 대한 부분을 **Filter**흐름에 따라 처리
- Dispatcher Servlet으로 가기전에 가장 먼저 적용 받음
- Interceptor는 Dispatcher와 Controller 사이에 위치함
- 장점으로는 보안관련 체계적으로 많은 옵션을 제공해 주어서 로직을 작성하지 않아도 된다는 장점

### Filter, Interceptor, AOP
- 비슷한데 무엇이 다를까?

<img src="https://user-images.githubusercontent.com/92348108/165003304-b737bd25-c5d7-44c0-884b-7600ab811b13.png" />

- 요청이 들어오면 Filter => Interceptor => AOP => Interceptor => Filter 순으로 거친다
1. 서버를 실행키셔 Servlet이 올라오는 동안 init()이 실행되고 doFilter가 실행된다
2. Controller에 들어가기전 preHandler가 실행된다
3. Controller에서 나와 postHandler,after Completion, doFilter순으로 진행된다
4. 서블릿 종료시 destroy가 실행된다.

## Spring Security

<img src="https://user-images.githubusercontent.com/92348108/165018859-ff75569e-f4e4-4ff4-9e3b-45fc24150f0f.png" />


### SecurityContextHolder
- 보안 주체의 세부 정보를 포함하여 현재 보안컨텍스트에 대한 세부 정보가 저장

### SecurityContext
- Authentication을 보관하는 역할, SecurityContext를 통해 Authentication 객체를 꺼내옴

## Authentication
- 현재 접근하는 주체의 정보와 권한을 담은 인터페이스
- SecurityContextHolder를 통해 SecurityContext에 접근하고, SecurityContext를 통해 Authentication에 접근함