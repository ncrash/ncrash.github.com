---
layout: post
title: "mac osx knowhow"
description: ""
category: osx
tags: [mac,osx,tip,setting,guide, ql, quicklook]
---
{% include JB/setup %}

부제 : Java 웹 개발자를 위한 OS X 환경 셋팅

---

## OS X & iOS 관련 블로그, 뉴스, 커뮤니티

* 국내
  * [Back to the Mac](http://macnews.tistory.com)
  * [Project Research | 카테고리 보관물 | Mac](http://projectresearch.co.kr/category/mac/)
* 해외
  * [9to5Mac: Apple iPhone, Mac and iPad News Breaking All Day](http://9to5mac.com/)
    * [뉴스레터 구독하기](http://feedburner.google.com/fb/a/mailverify?uri=9To5Mac-MacAllDay)
  * [OS X Daily - News and Tips for Mac, iPhone, iPad, and Everything Apple](http://osxdaily.com)
    * [뉴스레터 구독하기](http://feedburner.google.com/fb/a/mailverify?uri=osxdaily&loc=en_US)
* 커뮤니티
  * [클리앙 소모임 > MaClien](http://www.clien.net/cs2/bbs/board.php?bo_table=cm_mac)

---

## 시스템

### QuickLook

* *[훑어보기(QuickLook) 소개 - 개발자에게 추천하는 OS X 훑어보기(QuickLook) 플러그인 6종 + α](http://macnews.tistory.com/830)*
* [BetterZip Quick Look Generator](http://macitbetter.com/BetterZip-Quick-Look-Generator/)
  * ![BetterZipQL QuickLook](http://macitbetter.com/img/BetterZipQL11.jpg "BetterZipQL QuickLook")
* [MultiMarkdown QuickLook Generator](http://multimarkdown.com/download/)
  * [![](https://v4s2.yimg.com/so/7305/12959318634_fc5f0f7d11_z.jpg)](http://www.flickr.com/photos/dkkang1018/12959318634/)
* [qlImageSize](https://github.com/Nyx0uf/qlImageSize)
  * ***Mavericks에서 png, jpg, gif 파일에 대해 제대로 동작하지 않음. 대신 tga,bmp,psd,tif는 정상 동작***
  * ![qlImageSize 설치 전](http://static.whine.fr/images/2012/ql1.jpg "qlImageSize 설치 전")
  * ![qlImageSize 설치 후](http://static.whine.fr/images/2012/ql2.jpg "qlImageSize 설치 후")	
* [QLStephen](http://whomwah.github.io/qlstephen/)
  * ![QLStephen ScreenShot](http://farm4.static.flickr.com/3525/3195752859_e79137f720.jpg)
* [QuickLookJSON.qlgenerator](http://www.sagtau.com/quicklookjson.html)
  * ![QuickLookJSON ScreenShot](http://www.sagtau.com/media/screenshot.jpg "QuickLookJSON ScreenShot")

### Utility

* [iStat Menu](http://bjango.com/mac/istatmenus/)
* [Bartender](http://www.macbartender.com)
* [Paula](https://itunes.apple.com/kr/app/palua/id431494195?l=en&mt=12) - 프로그램에 따라 Function 키 맵핑을 할 수 있는 프로그램
  * ![Paula Preference](https://farm4.staticflickr.com/3833/12938871694_a7e0614618_z.jpg "Paula Preference")
* [Alfred](https://itunes.apple.com/kr/app/alfred/id405843582?l=en&mt=12)
  * Alfred 파워팩을 구입해야지만 Workflow 사용가능.. 대신 한번 손에 익으면 이것만큼 편한게 또 있을까 싶슴다.
  * Workflow - [알프레드 워크플로(Alfred Workflow) 어디서 받아야 할까? / Back to the Mac](http://macnews.tistory.com/2031)
    * [다음사전](http://www.clien.net/cs2/bbs/board.php?bo_table=cm_mac&wr_id=652636)
    * [Alfred2-google-workflow by zhaocai](http://zhaocai.github.io/alfred2-google-workflow/)
    * [Move to Dropbox](http://www.alfredforum.com/topic/460-to-dropbox-30-formerly-move-to-dropbox-url-to-the-clipboard/)
* [DaisyDisk](https://itunes.apple.com/kr/app/daisydisk/id411643860?l=en&mt=12)
  * [DaisyDisk 소개](http://macnews.tistory.com/1361)
  * SSD 시대를 살아가면서 효율적인 디스크 공간관리는 필수이며 손쉽게 튜닝(?)포인트를 찾을 수 있도록 도와주는 최고의 유틸리티
* [iTerm2](http://www.iterm2.com)
  * 기본으로 설치되어 있는 '터미널'에 만족하지 못한다면 확실한 '터미널' 대체제. 물론 유료인 SecureCRT가 좋긴하지만 비싸서 개인이 쓰기엔 힘들지 싶음
  * [oh my zsh](https://github.com/robbyrussell/oh-my-zsh) - Git, Rails 등의 플러그인을 제공하고 있어 유용
  * [iTerm2 custom folder Sharing Dropbox](http://blog.techstacks.com/2011/08/new-iterm-2-beta-released-today.html) - Dropbox를 통한 iTerm2 설정파일 클라우드 싱크
* [Go2Shell](https://itunes.apple.com/kr/app/go2shell/id445770608?l=en&mt=12)
  * [iterm2 연동](http://superuser.com/questions/434660/how-to-open-go2shell-preferences-in-mac-osx)
* [1Password](https://itunes.apple.com/kr/app/1password-password-manager/id443987910?l=en&mt=12)
  * 패워스드 관리 필수앱. 유명하니 자세한 설명은 패쓰
* [Forklift](https://itunes.apple.com/kr/app/forklift-file-manager-ftp/id412448059?l=en&mt=12)
  * 윈도우에서 TotalCommander를 주로 썼기 때문에 맥에서 유사한 기능을 해주는 유틸리티
  * 주로 쓰는 기능으로는 디렉토리별 파일 사이즈 계산 이것 밖에 없다.
  * 할인 행사($1.99)떄 구입을 해서 그런지 크게 돈이 아깝다는 생각 들지는 않지만 정가를 주고 구입하기엔 맥의 기본기와 유틸리티, 훑어보기등이 너무 좋아졌다. 

### Tip

* Eclipse 동시 수행
  * [Open multiple Eclipse workspaces on the Mac - Stack Overflow](http://stackoverflow.com/questions/118243/open-multiple-eclipse-workspaces-on-the-mac)
  * [OS X Eclipse Launcher 1.2.3](http://marketplace.eclipse.org/content/osx-eclipse-launcher#.Ue8iYhbLASd)
* 미팅, 발표에 도움이 되는 도구
  * [caffeine](https://itunes.apple.com/kr/app/caffeine/id411246225?l=en&mt=12) - (미팅 도중에 갑자기 잠들기 모드로 변경되는 난감한 상황을 피하고 싶을때 유용한)
  * [Keyboard Cleaner](http://jan.prima.de/~jan/plok/archives/48-Keyboard-Cleaner.html) - (키보드 청소용 유틸리티인데, 잠시 빔 프로젝터를 꺼둘때 유용한)

---

## 개발도구

### Programing Lanuage Reference

* [Dash](https://itunes.apple.com/kr/app/dash-docs-snippets/id458034879?l=en&mt=12)
  * ![Dash offers integration to any Mac OSX app](http://www.netsi.dk/wordpress/wp-content/uploads/2013/01/Dash-searchForSection.jpg "Dash offers integration to any Mac OSX app")
    * Image from : http://www.netsi.dk/wordpress/index.php/2013/01/15/dash-the-perfect-reference-too/
  * Dash에서 다운로드 받을 수 없었던 Spring Framework(최근에 추가됨) java docset 추가방법, 현재 Hibernate, MyBatis 등의 java docset은 없는 상태며 아래 방법으로 추가 가능
    * Spring Framework Docset이 필요해서 Dash 개발자에게 문의했더니 답변으로 알려준 내용
    * javadocset command로 Spring Documentation 사이트에서 배포 버전을 다운로드 받아서 api-docs 디렉토리를 docset 파일을 생성해서 Dash Docsets에 추가해주면 끝!
   >  
   >  === 문의 ===
   >  
   >  On 3 Jul 2013, at 01:38, Daekwon Kang <ncrash@me.com> wrote: 
   >  
   >  I'd like to request a docset for Spring Framework
   >  
   >  === 답변 ===
   >  
   >  Hi Daekwon,
   >  
   >  I've recorded your vote towards a Spring docset. Currently, Spring has 6 votes. Please note that I don't generate docsets unless more people ask for them.
   >  
   >  You can, however, generate your own docsets by following the instructions at http://kapeli.com/docsets.
   >  
   >  Regards,
   >  Bogdan
* [Code Box](https://itunes.apple.com/kr/app/codebox/id412536790?l=en&mt=12)
  * 코드 스니펫을 쉽게 관리할 수 있도록 도와주는 유틸리티
  * Text Expander와 겹치는 부분이 있지만 태생이 다르며 특히 CodeBox에는 코드 스니펫 외에 Multiple Asset, Asset Notes, Tag등을 관리 할 수 있음
  * Text Expander는 용도가 아주 단순함
* [Text Expander](https://itunes.apple.com/kr/app/textexpander-for-mac/id405274824?l=en&mt=12)
  * 키보드 타이핑 생산성 극대화를 위한 필수 유틸리티. 특히 리눅스의 복잡한 명령어나 반복적으로 입력하는 git, svn 커밋메시지의 기본골격을 제공
  * //TODO 실제 시연화면 gif 혹은 QuickCast로 제공
* [TextMate](https://github.com/textmate/textmate)
* [Papers](http://www.papersapp.com/papers/)

### Documentation

* [Skitch](http://macnews.tistory.com/339)
  * [주요 기능들이 몽땅 제거된 Skitch 2.0 대신 1.X 최종 버전 사용하기 (다운로드) / Back to the Mac](http://macnews.tistory.com/339)
  * [스키치(Skitch)로 스크린샷 이미지의 특정 영역 강조하기 / Back to the Mac](http://macnews.tistory.com/1063)
* [GifBrewery](https://itunes.apple.com/kr/app/gif-brewery/id435989461?l=en&mt=12)
  * [동영상 파일을 편집하고 GIF 애니메이션으로 변환할 수 있는 'GifBrewery' / Back to the Mac](http://macnews.tistory.com/2053)
* 2800 Icons for Facebook and Twitter - https://macappsto.re/kr/lHe3U.m
  * [어떤 용도로든 맘껏 쓸 수 있는 3천여개의 아이콘을 담은 앱 '2800 Icons for Developer' / Back to the Mac](http://macnews.tistory.com/1932)

---

## 기타

* Markdown
  * [Sublime Text 2](http://www.sublimetext.com/2) + [Marked](https://itunes.apple.com/kr/app/marked/id448925439?l=en&mt=12)
    * Package Control
    * Markdown Preview
    * Markdown Editing
    * Marked.app Menu
  * Confluence wiki에 Markdown으로 작성한 내용 적용방법
    * Marked 등과 같이 Markdown Preview 된 HTML을 복사한 후 Rich Text 타입으로 붙여넣기