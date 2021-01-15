# learning_spring

### 스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술
<br/>

## 프로젝트 환경설정
#### 프로젝트 생성
* 스프링 부트 스타터 사이트 <https://start.spring.io> 에서 스프링 프로젝트 생성

#### 라이브러리
* Gradle은 의존관계가 있는 라이브러리를 함께 다운로드함

#### View 환경설정
* 스프링 부트가 제공하는 Welcome Page 기능  
    * `static/index.html` 을 올려두면 Welcome page 기능 제공
* 템플릿 엔진
    * 템플릿 양식과 특정 데이터 모델에 따른 입력 자료를 결합하여 원하는 결과 문서를 출력하는 소프트웨어(또는 컴포넌트)
    * thymeleaf 템플릿 엔진 사용
* 컨트롤러에서 리턴 값으로 문자를 반환하면 `viewResolver`가 화면을 찾아서 처리함
    * 스프링 부트 템플릿 엔진 기본 viewName 매핑
    * `resources:templates/ + {ViewName} + .html`
    
#### 빌드 & 실행
1. `./gradlew build`
1. `cd build/libs`
1. `java -jar {Name}.jar`

<br/>
   
## 스프링 웹 개발 기초
#### 정적 컨텐츠
* 스프링 부트는 `resources:static`디렉토리에서 정적 컨텐츠 제공
  * controller 우선순위가 높음
  * ex) localhost:8080/hello-static.html -> hello-static 관련 컨트롤러가 없으므로 resources:static/hello-static.html을 찾아 반환
  
#### MVC
* Model, View, Controller
* 사용자 인터페이스로부터 비즈니스 로직을 분리

#### API
* `@Response`를 사용하면 HTTP BODY에 문자 내용을 직접 반환
  * viewResolver 대신  `HttpMessageConverter`가 동작
  * 객체를 반환하면 객체가 JSON으로 변환됨
  
<br/>

## 예제
#### Test
* JUnit 프레임워크로 테스트 실행
* `src/test/java` 아래 작성
* 테스트는 각각 독립적으로 실행되어야 함. (의존관계 X)   
* Annotation
  * `@Test` : 테스트 메소드 위에 작성
  * `@BeforeEach` :  각 테스트 실행 전에 호출
  * `@AfterEach` : 각 테스트가 종료될 때 마다 호출
  
<br/>

## 스프링 빈과 의존관계
* 스프링 빈을 등록하는 2가지 방법
  * 컴포넌트 스캔과 자동 의존관계 설정
  * 자바 코드로 직접 스프링 빈 등록하기
  
#### 컴포넌트 스캔과 자동 의존관계 설정
* 컴포넌트 스캔 원리
  * `@Component`가 있으면 스프링 빈으로 자동 등록됨
  * `@Controller`, `@Service`, `@Repository`는 `@Component`를 포함하기 때문에 스프링 빈으로 자동 등록됨
  * 스프링은 스프링 컨테이너에 스프링 빈을 등록할 때, 기본으로 싱글톤으로 등록한다.
* Dependency Injection (DI)
  * 객체 의존관계를 외부에서 넣어주는 것
  * 생성자에 `@Autowired`가 있으면 객체 생성 시점에 스프링이 해당 스프링 빈 스프링 컨테이너에서 찾아 넣어줌
  * `@Autowired`를 통한 DI는 스프링이 관리하는 객체에서만 동작  
  * 생성자가 1개만 있으면 `@Autowired` 생략 가능
  
#### 자바 코드로 직접 스프링 빈 등록하기
* `@Configuration`, `@Bean` 사용

