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
  
  
