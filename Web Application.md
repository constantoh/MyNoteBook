# Web Application
## 웹 - HTTP
> Client — internet — Server  

+ 통신 종류
	1. 정적 리소스 (HTML, 이미지, 영상)
	2. 동적 리소스 (HTML)
		1. SSR - Server Side Rendering -> jsp, 타임리프(템플릿 엔진)
		2. CSR - Client Side Rendering -> React, Vue
	3. DATA (HTTP API) [JSON]
- - - -
## 웹서버,  WAS
> 웹서버 	: 정적(Nginx, Apache), 고정 HTML, CSS, JS, 이미지, 영상  
> WAS 	: 동적(Tomcat)  

> 둘의 경계는 모호함. 웹서버에서도 WAS의 기능을, WAS에서도 웹서버의 기능을 수행할 수 있다.  

> 장애, 확장, 효율성으로 인해 웹서버, WAS를 구별하여 사용하는게 일반적  

** ~Client -> WebServer -> WAS -> DB~ **
- - - -
## Servlet
- Client에서 Server로 요청이 들어와 이를 처리하고 응답할 때 서버가 해줘야하는 일들은 굉장히 많고,  공통적인 부분이 많다 -> 이를 **Servlet**이 대체. 

- Java의 Annotation을 사용한다.
	+ @WebServlet
		+ name = 이름
		+ urlPatterns = 해당하는 URL이 호출되면 해당 서블릿을 호출 & service메소드 호출

-  HTTP 요청, 응답 정보를 편리하게 사용할 수 있게 HttpServletRequest, HttpServletResponse를 제공한다. 
	+ HttpServletReqeust 임시 저장소기능, 세션 관리 기능
	+ HttpServletResponse 쿠키, redirect

- Tomcat처럼 WAS에서 서블릿을 지원하는 WAS를  서블릿 컨테이너.
	- 서블릿 객체는 **싱글톤**으로 관리한다.
	+ 서블릿 객체를 생성, 초기화, 호출, 종료하는 생명주기를 관리한다.
	+ 멀티 쓰레드 처리를 지원한다.
		+ 동시 요청 처리 가능.
		+ 생성 비용, 문맥 교환 비용
		-> Thread Pool을 생성하여 관리.
- - - -
## JSP
- jsp는 서버 내부에서는 서블릿으로 변환된다.
- jsp는  `<%@ page contentType=“text/html;charset=UTF-8” language=“java” %>` 으로 시작되어야한다.
- jsp의 <%@ %>, <%= %> 안에서는request, response 객체를 사용할 수 있다.
& 객체는 response에 담겨있다.
- 
- - - -
## 서블릿과 jsp의 한계
> 서블릿에서 비즈니처리, 화면출력을 하던 것을, jsp를 사용하여 화면을 구성하는것을 보다 쉽게 처리할 수 있어졌다. 하지만 여전히 비즈니스처리, 화면 출력 등 jsp에서 너무 많은 역할을 한다. & 유지보수가 힘들다.  
> -> MVC패턴이 등장  
> -> -> 비즈니스 로직은 서블릿, jsp는 화면을 그리는 일에 집중.  
- - - -
## MVC
### Controller : HTTP요청을 받아서 파라미터를 검증 & 비즈니스 로직 실행. View에 전달할 결과 데이터를 조회해서 모델에 담는다.
####   Service : Controller에서 비즈니스로직을 분리

### Model : View에 출력할 데이터를 담는다. 그래서 View입장에서는 아무것도 알지못해도 Model에서 가져다 쓰면 된다.

- dispatcher.forward -> 새로운 요청없이 내부 메소드 호출하는 식으로 다른 화면으로 이동한다. url변경이 없다.
- redirect -> 실제 클라이언트에 응답이 나갔다가, redirect경로로 다시 요청이 들어오게끔 한다. url변경이 일어난다.
- - - -
## MVC 패턴의 한계
- MVC패턴을 적용하여 역할을 명확하게 구분하였음.
- 하지만,  컨트롤러들을 보면 중복이 너무 많다.
	- forwad
	- viewPath
- request, response 객체를 사용하지 않을 수도 있다.
- 공통처리가 어렵다.

-> 프론트 컨트롤러 도입 ( Front Controller )
- - - -
## Front Controller
- 모든 요청을 FC 하나로 받는다.
- FC를 제외한 컨트롤러는 Servlet을 사용하지 않아도 된다.
- 스프링 MVC의 핵심도 바로 FC. DispatcherServlet이 FC패턴으로 구현되어 있음.

### Controller가 Servlet종속성을 제거하려면 request, response 사용하지 않게 해야한다 -> Model 을 사용하자.
- - - -
## 스프링 MVC
-  **DispatcherServlet** : 스프링의 FrontController
- 핸들러 매핑으로 핸들러 조회(**Handler Mapping**)
 	- 1순위가 RequestMappingHandlerMapping
- 핸들러를 사용할 핸들러 어댑터 조회(**Handler Adapter**)
	- 1순위가 RequestMappingHandlerAdapter
- 핸들러 어댑터 실행
- ViewResolver
	- InternalResourceViewResolver - forward
	- Thymeleaf -> ThymeleafViewResolver

- - - -
## Web Application 개발 흐름
서블릿 -> JSP -> 서블릿 & JSP (MVC) -> MVC Framework -> Spring MVC -> Spring Boot