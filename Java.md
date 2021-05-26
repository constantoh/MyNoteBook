# Java
## HashMap
멀티쓰레드 환경에서는 동시성 문제가 있음 -> ConcurrentHashMap을 사용하길 추천

- [x] Generic 사용시 new 구문에 타입을 지정하지 않아도 되는 이유 ?
`Map<Long, Member> *store*= new HashMap<>();`
->  JDK 1.7 부터는 ~추정이 가능~ 한 경우 타입을 생략할 수 있게 되었다.
 	- 참조변수의 타입으로 Long, Member의 타입을 추정할 수 있다.
 	- 