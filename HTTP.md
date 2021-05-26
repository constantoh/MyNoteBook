# HTTP
## 데이터 전달하는 방법
- GET - 쿼리 파라미터
	+ url?~
- POST - HTML form
	+ ~content-type~: application/x-xxx-form-urlencoded
	+ 메세지 바디에 쿼리 파라미터 형식으로 전달됨 -> request.getParameter 로 사용
- HTTP message Body에 데이터를 담아 전달.
	+ JSON
> JSON의 결과를 객체를 변환하려면 Jackson, Gson과 같은 JSON 변환 라이브러리를 사용해야함. 스프링 부트로 Spring MVC를 선택하면 Jackson 라이브러리를 함께 제공함.(ObjectMapper)   

	