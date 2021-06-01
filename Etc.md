# Etc
##  CI / CD
- CI : 
- CD :  

## Jpa
- d

## Gradle
> 빌드 도구  

- build.gradle :  


## GroupID / ArtifactID 
 - GroupID : 그룹명
 - ArtifactID : 프로젝트명

## 템플릿 엔진
- 초기 Servlet만 사용하던 시절에 자바코드로 응답HTML 소스를 구성하는 방법을 사용했다. -> 이를 HTML소스에서 javat소스를 사용할 수 있게 하여 보다 편리하게  사용하고자 탄생되었음 ( JSP, Thymeleaf, Freemarker, Velocity )

## /WEB-INF
- 이 경로안에 있는 jsp는 외부에서 호출할 수 없다. 항상 컨트롤러를 통해 jsp를 호출하게끔 위한 전략

## Jar, War
 - Jar 
 	- 내장 서버 사용에 최적화
 	- /resources/static/index.html 파일을 Welcome 페이지로 사용 가능.
 	- webApp 경로 사용 X, 정적 리소스도 클래스 경로에 함꼐 포함해야함.
 - War  : webApp 경로를 사용, 주로 외부 서버 배포시 사용

## 로깅
- 로깅 라이브러리 : 스프링 부트 라이브러리에 포함(spring-boot-starter-logging)
- SLF4J : 인터페이스
- Loback : 구현체
- @SLF4J 롬복 Annotation 사용 가능
- 사용 법 `log.debug(“data={}”, data)` 
	- 스트링 연산이 일어날 수 있는 + 연산은 쓰지 않는다.
	- 

  