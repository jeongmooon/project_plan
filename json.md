# JSON(JavaScript Object Notaion)
- 오브젝트를 표현하는 문자열(key-value)
- 서로 이해할 수 있는 형태로 변환해야 하는 데 변환 하는 작업이 직렬화

# Spring Initializr 사용
- Project : 생성할 프로젝트의 빌드 자동화 툴 선택(Maven, Gradle)
- Language : 사용할 언어(kotlin, Java)
- Spring Boot :
    - 생성할 부트 버전 선택
    - sanpshot은 아직 개발 중이여서 오늘이나 내일이나 버전이 다를 수 있다는 뜻
    <a href="https://stackoverflow.com/questions/46786486/alpha-beta-snapshot-release-nightly-milestone-release-candidaterc-whe/46967235#46967235">참고 사이트</a>
- Prodject MetaData :
    - Group과 Aritfact는 후에 프로젝트를 배포하는 경우 프로젝트가 무슨 프로젝트인지 묘사하는데 사용
    - Public Repository에 배포하는 것이 아닌 기본으로 들어가 있는 Group과 Artifact를 사용
    - Packaging에는 Jar, Java 버전..
- Dependencies :
    - Spring Initalizr에서는 필요한 디펜던시를 추가 가능
    - 추가된 디펜던시는 maven,gradle에 추가됨
    - Spring Web,Spring Data JPA,H2 Database, Lombok.....
    - 추가 라이브러리 느낌

# Spring
# Application.java
- @SpringBootApplication : 베이스 패키지 선언
    - 의존성이 필요한 경우 찾아서 연결해줌(@Autonwired)
    - componentScan이 필요한데 어떻게 하는가??
    - 우리가 사용하는 @Controller, @Service, @repository 등은 내부에 @Component를 가지고 있어서 스캔이 가능한것이 였다.

    - @SpringBootApplication 어노테이션 내부..

    ```    
    @ComponentScan
    public @inerface SpringBootApplication {
        ....
    }
    ```

    - 이런식으로 코드가 짜여 있어서 스캔을 추가 해주지 않아도 어노테이션을 찾아내는 것(xml에서 기술하던거...)
    
    - 만약에 자동으로 오브젝트를 생성하고 싶지 않았을 경우에는??
    - @Bean 을 사용

# build.gradle

```
group = 'com.example'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '17'
```

- group은 어플리케이션으ㅓㄹ 배포하는데 사용
- vesion 프로젝트 버전
- source.. 자바 버전

## Dependency
- 이 프로젝트에서 사용할 라이브러리 명시하면 설치해줌(packge.json 느낌)

## Test
- 유닛 테스트

# Layered Architecture
