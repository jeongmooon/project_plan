# spring Security

## Spring Security?
- 애플리케이션의 보안(인증과 권한, 인가 등)을 담당하는 스프링 하위 프레임워크
- **'인증'과 '권한'**에 대한 부분을 **Filter**흐름에 따라 처리
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

### Authentication
- 현재 접근하는 주체의 정보와 권한을 담은 인터페이스
- SecurityContextHolder를 통해 SecurityContext에 접근하고, SecurityContext를 통해 Authentication에 접근함

### UsernamePasswordAuthenticationToken
- Authentication을 implements한 AbstractAuthenticationToken의 하위 클래스로, User Id가 Principal역할을 하고, Password가 Credential 역할
- UsernamePasswordAuthenticationToken의 첫 번째 생성자는 인증 전의 객체를 생성, 두번째 생성자는 인증이 완료된 객체를 생성

### AuthenticationProvider
- 실제 인증에 대한 부분 처리하는 곳
- 인증 전의 Authentication객체를 받고, 인증이 완료된 객체를 반환하는 역할
- 인터페이스를 구현해서 Custom한 AuthenticationProvider를 작성하고, AuthenticationManager에 등록

### AuthenticationManager에
- 이곳에 등록된 AuthenticationProvider에 의해서 인증처리가 됨
- 인증이 성공하면 2번째 생성자를 이용해 인증이 성공한 객체를 생성하여 SecurityContext(session?)에 저장
- 인증상태를 유지하기 위해 세션에 보관, 인증이 실패하면 AuthenticationException 발생

- Custom매니저를 등록하기 위해서는 **WebSecurityConfigurerAdapter**를 상속하여 등록한다

### UserDetails
- 인증에 성공하여 생성된 UserDetails 객체는 Authentication객체를 구현한 UsernamePasswordAuthenticationToken를 생성하기 위해 사용
- UserDetails 인터페이스는 이런 method를 가지고 있다

```
public interface UserDetails extends Serializable {
     Collection<? extends GrantedAuthority> getAuthorities();
     String getPassword(); String getUsername();
     boolean isAccountNonExpired();
     boolean isAccountNonLocked();
     boolean isCredentialsNonExpired();
     boolean isEnabled();
}

```

### UserDetailsService
- 이 인터페이스는 UserDetails객체를 반환하는 단 하나의 메소드만 가지고 있음
- 이를 구현한 클래스의 내부에 UserRepository를 주입받아 DB와 연결하여 처리함

```
public interface UserDetailsService {
    UserDetails loadUserByUsername(String var1) throws UsernameNotFoundException;
}
```

### PasswordEncoding
- AuthenticationManagerBuilder.userDetailsService().passwordEncoder() 로 암호화에 사용될 비밀번호 지정

### GrantedAuthority
- 현재 사용자가 가지고 있는 권한, roles로 구현
- GrantedAuthority객체는 UserDtailsService에 의해 불러올 수 있고, 특정 자원에 대한 권한이 있는지 검사하고 접근 허용 여부 결정
