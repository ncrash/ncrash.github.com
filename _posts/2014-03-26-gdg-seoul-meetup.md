---
layout: post
title: "GDG Seoul 2014년 3월 정기 Meetup"
description: ""
category: 
tags: [vagrant, docker]
---
{% include JB/setup %}

* 신청페이지 : [https://developers.google.com/events/5228281527795712/](https://developers.google.com/events/5228281527795712/)
* 이벤트페이지 : [https://plus.google.com/events/cao3hh6tkm1n9uqvjc8thf12klc](https://plus.google.com/events/cao3hh6tkm1n9uqvjc8thf12klc)
* 발표자료
    * Docker
        * [http://www.slideshare.net/modestjude/about-docker-in-gdg-seoul](http://www.slideshare.net/modestjude/about-docker-in-gdg-seoul)
        * [https://github.com/judeKim/_develop](https://github.com/judeKim/_develop)
    * AOSP : [https://github.com/chitacan/aosp-build-with-vagrant](https://github.com/chitacan/aosp-build-with-vagrant)
* 일자 : 2014년 3월 26일(수)
* 시간 : 7:00pm - 10:00pm
* 장소 : D.CAMP

---

## AOSP(Android Open Source Project)

* 텍스트 파일 기반으로 가상머신을 구성
* 다양한 OS 지원 box.es
* 1.5에서 vagrant share, vagrant cloud
    * share
        * 포트 포워딩된 서비스를 외부에 서비스 할때
    * cloud
* tmux +_+;
* // TODO vim에서 Vagrantfile syntaxhighlight 
    * cpu, mem 설정이 눈에 띔
    * 필요한 내용만 압축하니 pt 장표 한장에 모두 표현할 수 있다는 점 좋다. pt 꼭 얻어야 겠네..
* Provisioning
    * 시스템 구성과 관련된 일들을 처리
    * shell, chef, puppet
    * puppet은 github이 boxen 쓰고 chef는 페북이 쓴다고.. 
    * puppet
        * file { content와 source의 차이점 이해
* box는 vagrant cloud에서 가져다 사용할 수 있다? 확인 필요..
    * hashicorp/precise64
* // TODO  pt에서 소스코드 스크롤이 되는데 멋지다 +_+
* github chitacan aosp-env
* shell도 배우고 싶다. 
* hmm
    * cgrep : c source grep
    * jgrep : java source grep
    * resgrep : xml grep
    * godir : depth가 깊은 directory를 찾아들어갈 때 유용한 도구
* pt는 http://lab.hakim.se/reveal-js 만들어서 소스코드 스크롤이 가능했던것..

---

## Lightweight Linux Container Docker를 활용한 개발 환경 구축하기


* python -> go 언어로
* dotCloud 내부 프로젝트로 시작(2013.01)
* 상당히 빠르게 전개되고 있는 프로젝트
* deview 발표자 : judekim
* // FORK NxM Matix dependency 멘붕 
* run everwhere
    * 리눅스 커널에서 제공하는 기능.. 
* // FORK docker before after 장표로
* docker는 api 덩어리
    * 래핑을 해둔 녀석
* docker 핵심
    * lxc
        * namespaces
        * cgroups
    * layerd file system
        * aofs
        * 최근에는 다양한 파일 시스템도 선택적 지원되고 있다고... 
    * 컨테이너가 아주 가벼운 vm 역활을 할 수 있는것
* 타입??
    * Hypervisor Type2 : virtual box, vmware
    * vm은 host 위에 올라가는 것
    * docker ...
        * mac에서는 vagrant를 통해 ubuntu 64bit 위에 docker를 돌리는 것
        * 즉 ubuntu가 host
        * 그리고 docker child instance에서 docker ps 실행 시 부모 os process 확인이 가능한 것
* 커널 이슈
    * 3.8 이상이 되야 정상적으로 동작한다고…
* 동작확인
    * netstat -nat
        * 호스트(0.0.0.0)에서 서비스 되는 프로세스 확인 가능?
* busybox
    * 가장 가벼운 리눅스 이미지
* vagrant와의 성능 비교
    * echo hello world
    * docker : 1초
    * vagrant : 최소 1분
    * //TODO vagrant 소개 마무리에 써먹어야지!!
* docker 경량화의 비법
    * 핵심은 델타.. 
        * git과 비슷한데…
    * 파일 변화의 변경내역이 델타에 다 남아 있다는 것
* 클라우드 서비스에서도 docker를 지원
    * amazon ec2, rackspace, google cloud
    * docker의 가능성으로 인해 클라우드에서도 발 빠르게 지원
    * 발표자가 baas.io 프로젝트 진행 시 docker 활용했었다고…
* https://index.docker.io
    * public 지원
        * private는 별도로 repository daemon을 제공하고 있다고
    * 샘플은 mysql로 진행
* docker command
    * ps
        * container가 어떻게 떠있는지 확인
    * images
        * 이미지 리스트
    * pull 
        * https://index.docker.io 에서 이미 빌드된 이미지를 다운로드 받을때
* vagrant vs docker
    * vagrant는 vm(virtual machine)
    * docker는 ve(virtual environment)
* apache in ubuntu 12.04 docker
    * docker는 실행을 foreground를 띄워야 동작한다는 점을 유의
    * 자식 instance를 만들면 스냅샷… 반드시 커밋해서 이미지를 만들어야지 저장됨
* 개발환경 구축
    * 기존 개발환경
        * vagrant를 활용한 다중 vm을 사용
    * https://github.com/judeKim/_develop
* docker 실행하기
    * port 1~1024 previlged? 영역이라 루트권한이 필요한것.. 해서 docker 실행 시 옵션을 줄 수 있음
* mysql
* 유의사항
    * hosts 파일은 아직 수정이 불가능하다. - 이슈 진행중… 성능에서 치명적.. 
    * host의 디렉토리 마운트 하는 경우 Dockerfile로 만들 수 없다.
    * 다중 daemon 을 띄우려면 우회적인 방법을 써야한다.
        * supervisor(?) 같은 녀석을 써야한다고…
* // FIXME host 파일 관리를 위해 Gas Mask 프로그램을 써서 관리하는 점이 특이..
* ~/private_workspace
    * 뭔지 딱 감은 오질 않지만 멋진데…
    * vagrant share directory 군