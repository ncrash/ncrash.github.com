---
layout: post
title: "나는 프로그래머다! - DB 튜닝의 모든 것 1부"
description: ""
categories: subway-study
tags: [subway,study,database,mysql,mariadb,tuning]
---

---

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

### 2부: mysql 튜닝 포인트 8가지
```일반적으로 DBMS 서버에 필요한 CPU, MEM, I/O 및 OS 튜닝 이슈에 대해서 살펴봅니다.```

* 웹서버 사양의 2배 이상은 갖춰야함. 웹서버는 증설만 하면 되기때문에 서버사양에 대한 큰 고민하지 않아도 됨
	* DB는 고사양으로 변경시 마이그레이션 이슈가 매우 크기때문에 초기에 신중하게 결정해야 함
* 저사양 BMT MySQL vs 오라클 결과는 MySQL. 이유는 오라클은 일정 사양 이상에서 쓰레드풀 활용으로 인한 성능이 나오기 때문
* 오픈소스 DBMS는 하드웨어빨이 중요하다
	* CPU 코어(칩셋은 최신), 메모리 용량(최대한 많이), 퓨전IO
	* 최대한 최신 아키텍쳐 하드웨어를 선택하는게 좋고 구버전과 신버전 차이만으로도 성능이 10% 차이가 날 수 있다고함
	* HDD < SSD < Flash SSD < Non Volilatal Memory < DDR 메모리
	* 리눅스는 하이엔드 사양이 아니다보니 메모리 200기가 이상꽂으면 제대로 성능이 나오지 않기에 커널튜닝 필요하기에 128기가 권장
* 클라우드
	* 하이엔드 인스턴스를 쓰시라
	* IO 성능 같은게 리인벤트 발표내용만큼 나오지 않고 있음. 특히 리전별로 성능차이가 발생하고 있음
	* 튜닝 시 유의사항 HyperVisor 레이어에서 하드한 튜닝은 막고 있어서 커널 파라미터 조정정도만 가능
	* vCore == Virtual Core
	* AWS RDS 관리와 운영이 편해 추천하지만 성능은 추천하지 않음
		* 성능을 비유하면 코로케이션에서 10대로 운영할거 20~30대 늘리는 식으로 생각해야함
* 튜닝
	* OS튜닝 : [레드햇 튜닝 가이드](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/pdf/Performance_Tuning_Guide/Red_Hat_Enterprise_Linux-7-Performance_Tuning_Guide-en-US.pdf), 델 튜닝 가이드를 참고해서 튜닝 진행
	* DB튜닝 : 오라클 설치 가이드를 MySQL에 그대로 적용 튜닝
* 요즘 장애대처 흐름
	* 장애는 필수불가결 요소라는 인식이 자리잡힘
	* 장애상황발생 시 얼마만큼 메뉴얼화 되어 있는지가 중요
	* MySQL 한대에서 성능최대로 뽑아낼려고 하는것 보다는 수평분할 하는걸 추천
* 스타트업
	* 초반에는 AWS RDS나 REDIS를 선택해서 운영이슈를 클라우드 업체에 믿고가는게 좋음
	* 카카오는 Redis를 선택했고 라인은 HDFS 선택
		* 서비스가 매우 커진다는 확신이 있다면 초반부터 아키텍쳐를 HDFS로 선택하고 구성하는게 맞지만 상대적으로 어렵긴함
	* 동접 100~200명 수준은 서비스는 그냥 클라우드 쓰는게 맞음
	* 망하지 않는 클라우드 벤더를 선택하는게 무척 좋음
* 꿀팁
	* 2권의 책([MySQL 성능 최적화](http://www.yes24.com/24/Goods/4348383?Acode=101), [리얼 MariaDB](http://www.yes24.com/24/goods/12653486)) 보는것
	* 네이버 MySQL 파워유저 카페 활동참여, 한달에 한번 세미나
	* [MySQL Performance Blog](https://www.percona.com/blog/) 성능튜닝 성지 +_+
	* [planet.mysql.com](http://planet.mysql.com/) MySQL 피드정리해서 공유
	* **[일본 사이트(오라클)](http://www-jp.mysql.com/) 들어가서 번역서비스를 통해 아티클 보면 정말 깔끔하게 볼 수 있음** 

### 3부: mysql 튜닝 포인트
```아르노 Adant 가 MySQL Connect 2013 에서 발표한 성능개선 50가지 팁에 대해서 살펴봅니다. ( Tip 1-13 )```

* 팁
	* 1번 메모리
	* 2번 CPU
	* 3번 디스크
		* Fusion IO가 비싸다면 짝퉁제품들이 많으니 대안이 되는 포인트 많음
	* 4번 OS
		* MySQL이 어디서 개발될까? 리눅스에서 개발됨으로 당연히 리눅스가 최상의 속도
		* 튜닝포인트가 전부 리눅스 기반으로 제공
	* 5번 리소스
		* open file 수랑 유저 쓰레드 수는 최대치로 설정
	* 6번 malloc
		* facebook jmalloc 지속적인 트래픽을 받아줘야 하는 서비스는 고려해볼만
	* 7번 linux cpu 오퍼니티(?)
		* 누마 컨트롤 인터렉티브하게 설정
		* 스왑은 죄악이다. 성능 저하의 주요원인
		* aws 클라우드에서는 적용이 쉽지 않은게 zen hypervisor단 제약으로 인해
	* 8번 파일 시스템파티션
		* xfs is excellent
		* 마운트 옵션 항상 체크
		* buffered io, checked io 벤치
		* SSD
	* 9번 
		* 리눅스 cfq 기본설정인데 deadline, nop를 많이 쓰는데 일반적으론 deadline 선택
		* 선택 시 항상 벤치성능 확인하고 결정
		* raid controller 이슈 없는지 잘 체크해야함
		* raid controller 깨지면 데이터 날라가는건 한순간이니 이중화나 백업 철저히
	* 12번
		* 로그와 데이터 디스크 분리
		* raid 스트라이핑 구성하는게 가장 성능상 좋음
	* 19번
		* 성능상 구려서 쿼리 캐쉬 꺼라
		* 옵티마이져 성능이 구려서 플랜짜는게 잘 맞지 않음
		* 쿼리 캐쉬 옵티마이져 Single Thread 동작방식이라 Bottle Lack 자주 걸림
		* 아예 꺼라
		* mysql보다 mariadb를 써라 스레드풀 때문에
		* 모니터링과 백업 때문에라도 엔터프라이즈 쓰는게 가장 최선
* 인프라 구성
	* 메모리 많이 구성 액티브 데이터에 비례하게 메모리를 구성
		* 32코어 구성할 시 코어당 메모리 2기가 또는 4기가 구성
	* temp 디렉토리를 디스크를 램디스크도 잡아야 성능상 이점을 누릴 수 있음
* 유의사항
	* 
* 참고 자료
	* http://blog.aadant.com
	* http://aadant.com/blog/wp-content/uploads/2013/09/50-Tips-for-Boosting-MySQL-Performance-CON2655.pdf
