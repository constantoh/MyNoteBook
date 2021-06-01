# Spring
## 스프링부트
- 스프링부트는 내장하고 있는 톰캣을 사용하여 웹서버를 설치하지 않고도 웹서버를 구축 할 수 있다.  -> jar파일을 실행하는것만으로 서비스를 실행할 수 있다.
#웹서버

## Annotation
- @RequestMapping : 요청정보 맵핑. 해당 URL이 호출되면 이 메서드가 호출됨.
	- RequestMappingHandlerMapping 
	- RequestMappingHandlerAdapter
		- 가장 우선순위가 높은 핸들러 매핑과 어댑터 
	- value = url, method = RequestMethod.GET, POST
	- GetMapping, PostMapping, …

- @Component : 컴포넌트스캔의 대상이되어 자동으로 스프링 빈으로 등록
	- Controller : 스프링MVC에서 Annotation 기반 컨트롤러로 인식됨.
	-> RequestMappingHandlerMapping에서 이 컨트롤러를 참조한다.
	- 
- RequestParam : request.getParameter(“”)와 같다.

- RestController : 컨트롤러의 반환 값으로 view를 찾는 것이 아니라, 바로 HTTP 메세지 바디에 입력한다.

- ResponseBody : RestController와 같이 메세지 바디에 직접 입력. method에 붙임.

- PathVariable : @PathVariable(“id”)로 사용하면 url에 해당 id값을 바로 받아 쓸 수 있다.




Model : 스프링에서 제공하는 Model

- [ ] 도메인 객체 설계시 기본 생성자 코드를 넣는 이유 ? 

