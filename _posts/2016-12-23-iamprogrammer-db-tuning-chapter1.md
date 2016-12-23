# [나는 프로그래머다!](http://pod.ssenhosting.com/rss/programmer/iamprogram.xml) 데니스채널 e02 - DB 튜닝의 모든 것 1부

## 이형채, "DB 장애를 내본 사람"	29:12 06/11/2016

###1부: MySQL 튜닝과 장애 대처

* 엑사데이터
	* 아이튠즈 사례 - 엑세데이터 서버 10여대
	* 소나타 vs 페라리 태생적 성능차이를 알아야 함
* mysql 쓰면서 가장 이슈가 되는게 모니터링과 백업 
	* 상용버전인 mysql enterprise로 해결이 가능하지만 비용이 만만치 않은것
* mysql
	* 개발자인 마이클 몬티 위드니우스 자녀가 1남 2녀. 자녀 이름을 따서 제품군을 만듬
	* 첫번쨰 버전은 첫번째 자녀의 이름을 따서 만든 것. SAP에 판매
	* 두번쨰 버전이 MySQL
	* 세번째 버전이 MariaDB
* [mariadb는 커뮤니티 버전에 쓰레드 풀 지원](https://mariadb.com/kb/ko/mariadb-vs-mysql-features/)
	* mysql enterprise 버전에서 제공되는 기능
	* 카카오도 mariadb를 채택해서 사용 중
	* 추천은 mariadb, mysql, 페르코나 순으로 추천
	* 서브스크립션 안쓸꺼면 mariadb가 최선, 그래도 서브스크립션 업체를 받아서 운영해 나가는걸 추천
* my.cnf
	* 남들이 잘해논걸 구하는게 성능튜닝 절반은 달성
		* 구글링과 github으로 좋은 사례를 구할수 있고 지인찬스를 쓰는것도 방법
	* MySQL 5.6에서는 default 값으로 mysql.cnf 잡혀져 있음
		* 이러한 상황으로 인해 default 값으로 사용하는 사람들이 생김
		* 오픈소스 특성상 low end pc 성능에도 동작하도록 되어 있어 파라미터 값들이 너무 낮게 책정되어 있어 고가용성 서비스에 적합하지 않음. 특히 클라우드에서 그냥 쓰는것 최악(죽음)
		* 예전에는 sample mysql.cnf 3가지정도 상황에 맞는 샘플을 제공해줬다고 함
* 성능 벤치 및 기준점
	* ROW는 1억건 이하, 테이블은 용량 1테라 이하인데 수백기가 이하를 권장
	* QPS(Query Per Second) - 웹 서비스에 적합한 성능 기준점
	* TPS(Transaction Per Second) - 금융권에 적합한 성능 기준점
	* 퓨전IO를 꼽았다면 메모리 100기가 이상 구성하고 80코어 정도로 구성
		* 최대한 마스터는 Scale Up으로 문제상황을 해결
		* Slave를 최대한 늘리라. 극한으로 가면 2 Tier로 구성
	* BMT 외부사례는 외부사례일뿐 자신의 환경에서 직접 돌려봐야 하는게 중요
	* 서버 조립에 대한 전수검사를 했다고 메모리를 꼽는것도 3, 4채널 구분해서 꼽고 잘못꼽으면 2채널만 사용하는 꼴이 된다고
* 정리
	* 서브스크립션과 기술지원
	* my.cnf를 잘 찾아서 적용하라

### 함꼐 읽어볼거리
* [카카오톡 메신저, 10배 빨라졌다는데… - 지디넷코리아](http://www.zdnet.co.kr/news/news_view.asp?artice_id=20130904102343&type=xml)
* [MariaDB - 위키백과, 우리 모두의 백과사전](https://ko.wikipedia.org/wiki/MariaDB)
* [공개SW(oss.kr) 오픈소스 기술지원기업 업체 리스트](http://www.oss.kr/oss_techsupportlist)
* [네이버 mysql 파워유저 카페](http://cafe.naver.com/mysqlpg)
