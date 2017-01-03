# [토비의 봄 TV 9회 스프링 리액티브 프로그래밍 (5) 비동기 RestTemplate과 비동기 MVC/Serlvet - YouTube](https://youtu.be/ExUfZkh7Puk)

* 쓰레드를 생성하는 작업자체가 비용이 상당히 들기 때문에 쓰레드 갯수를 무한정 늘릴수 없고 늘린다면 어느 한계상황에 다다르면 오히려 성능이 느려지고 메모리 오류발생도 있을 수 있다는 것
* 디폴트 쓰레드 갯수는 200개 정도
* 유명한 컨퍼런스에서 "이렇게 동작합니다"라고 얘기에 그냥 적용하기 보다는 직접 돌려보고 확인하는 습관이 굉장히 중요함
* 성능툴 - jmc(Java Mission Control)
	* 상용서버에 설치하게 되면 라이센스를 꼭 구매하고 써야함
	* 하지만 개발서버단까지는 괜찮다고 
* LoadTest.java 
	* ExecutorService Helloworld 코드 템플릿 quiver로 담아두자
	* ExecutorService 쓰레드 처리 시 순차적으로 쓰레드가 생성되는데 CyclicBarrier를 쓰게되면 요청처리를 한꺼번에 모아서 한방에 쏘는걸 해볼 수 있음
	* Callable, Runnable 차이점과 lambda에서 Runnable구조로 코드를 구성할 경우 Exception 처리상에 이슈가 있으니 Callable 구조로 구현하는게 유리한점 
* AsyncRestTemplate
	* Background Thread를 생성하고 비동기 처리하는 방식
	* jmc로 Live Thread Graph로 확인해보면 100개 쓰레드가 순간적으로 만들어지는걸 확인해볼 수 있음
	* Netty4ClientHttpRequestFactory로 구현체를 갈아끼울 수 있고 쓰레드 갯수를 조정해 쓰레드 하나로 돌리는것 가능
	* DeferredResult를 통해 Callback 형태로 결과값을 처리하는 방식
* **비동기를 잘 활용하면 메모리 사용량 최소화 가능**
* 비동기로 DB 액세스 처리는 기본적으로 JDBC이고 메소드 정의자체가 동기적으로 작성되어 있기에 불가능. 하지만 비동기 드라이버를 제공해주는 몽고디비와 같은 NoSQL쪽은 비동기 방식(넌블럭킹)으로 사용할 수 있도록 제공해주고 있음
	* 오라클이 비동기 JDBC 스펙을 만들기 시작. 자바9에는 들어가지 못할것
	* 들어간다면 자바10에 비동기 JDBC를 사용할 수 있게 될것
	* Spring Data를 보면 NoSQL쪽은 비동기를 지원하는 코드를 볼 수 있다는것

## 정리

* 이번회차에 나온 코드를 리액티브 방식으로 개선해나가는 다음시간에 진행해볼 것
* 질문은 가능하면 Slack 채널을 통해서 질문달기
* 피드백과 관심 그리고 후기 등등 응원하기

## TODO

[] Class 언급된것 링크달기
[] 샘플 소스코드 작성해보기