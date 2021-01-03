---
title:  "닷홈을 이용한 APM 웹개발 환경 설정"
excerpt: ""

categories:
  - Web
tags:
  - Web
  - APM
last_modified_at: 2021-01-01 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

### 1. 웹 서버 설정하기

#### 웹 시스템

우리가 매일 사용하고 있는 인터넷을 구성하는 시스템을 웹 시스템(web system)이라고 한다. 이러한 웹 시스템은 아래의 그림과 같이 클라이언트(client)와 서버(server)로 구성된다.

![dothome](/assets/images/dothome_setting.img_php_web_system.png)

서버란 간단히 말해 웹 서비스를 제공하는 컴퓨터를 의미한다. 클라이언트란 서버가 제공하는 웹 서비스를 이용하는 사용자 또는 사용자의 기기(브라우저)를 의미한다.

#### 웹 서버

웹 서버는 HTTP를 통해 웹 브라우저에서 요청하는 HTML 문서나 이미지 파일 등을 전송해주는 서비스 프로그램을 말한다. 웹 서버 소프트웨어를 구동하는 하드웨어도 웹 서버라고 하기도 하지만 일반적으로 웹서버라고 하면 소프트웨어를 의미한다. 웹 서버의 주된 기능은 웹 페이지를 클라이언트로 전달하는 것이다. 주로 그림, CSS, 자바스크립트를 포함한 HTML문서가 클라이언트로 전달된다. 주로 콘텐츠를 제공하지만 클라이언트로부터 콘텐츠를 전달 받기도 한다. 이러한 기능은 파일 업로드를 포함하여 클라이언트에서 제출한 웹 폼을 수신할 때 쓰인다. 

- 대부분의 웹 서버는 이러한 공통 기능을 가지고 있다.
  1. HTTP
  2. 통신 기록

-  웹 서버는 다음과 같은 기능도 제공한다.
  1. 인증
  2. 정적 콘텐츠 관리
  3. HTTPS 지원
  4. 콘텐츠 압축
  5. 가상 호스팅
  6. 대용량 파일 지원
  7. 대역폭 스로틀링

#### APM

- Apache 

  - Apache는 세계적으로 많이 쓰이는 웹 서버용 소프트웨어이다. Apache는 Apache재단에서 만든 정적 HTTP서버이다. Apache는 굉장히 다양하고 기능적인 면에서 우수하다. 또 구축이 쉽다는 이유 때문에 많이 사용한다. 단, Apache자체만으로 엄청 무겁고 , Squid와 함께 Slowloris취약점이 발견되었기에 , 보통 프로그래밍 능력이 능숙한 사람들이나 , 대형사이트 운영자는 Nginx , IIS를 주로 사용을 한다. 하지만 대부분의 중소기업들은 무료이기때문에 많이 사용을 한다. 아파치는 많은 운영체제에서 운용할 수 있다. BSD , 리눅스 등 [Unix ](https://blog.naver.com/sincc0715?Redirect=Log&logNo=221806244606&from=postView)계열 뿐만 아니라 우리가 사용하는 마이크로소프트 윈도우 등 여러 기종에서 사용이 가능하다.  
  - Tomcat 역시 Apache 재단에서 만든 서버이다. Tomcat은 Apache와 달리 동적인 데이터를 처리하는 웹서버이다. 동적 웹 서버는 WAS(Web Application Server) 라고 불리며, 웹서버와 웹 컨테이너의 결합으로 다양한 기능을 컨테이너에 구현하고 다양한 역할을 수행할 수 있는 서버이다.

- PHP

  - PHP는 서버 측에서 실행되는 프로그래밍 언어로 HTML을 프로그래밍적으로 생성해주고, 데이터베이스와 상호작용 하면서 데이터를 저장하고, 표현한다. PHP는 웹을 위해서 만들어졌고, 지금도 웹을 위해서 발전하고 있는 웹을 위한 언어이다. PHP는 웹프로그래밍을 위한 높은 생산성을 제공하는 언어이다. 특히 서버에 직접 설치해서 운영할 수 있는 설치형 웹에플리케이션(제로보드,텍스트큐브,워드프래스,PHPBB등)의 과반이 PHP로 만들어졌다. PHP의 장점은 이 언어를 배워놓으면 이러한 솔루션들에 대한 운영, 문제해결 능력이 향상된다는 점이고 무엇보다 쉽다.  

- MySQL

  - MySQL은 세계에서 가장 많이 쓰이는 오픈 소스의 [관계형 데이터베이스 관리 시스템](https://ko.wikipedia.org/wiki/관계형_데이터베이스_관리_시스템)(RDBMS)이다

  - DB(Database)

    - 데이터를 저장하는 공간으로 DB를 통해 효율적으로 데이터를 저장하고, 검색하고, 정렬하며, 탐색할 수 있다. 

  - SQL

    \- Structured Query Language의 약어로 구조화된 질의를 위한 언어라는 뜻이다. 즉, DB에 질의(Query)하기 위한 언어이다.

  - MySQL 특징 

    1. 동작이 빠르다.

    2. 오픈 소스

    3. 여러 운영체제에서 동작

    4. 많은 프로그램 언어 지원

    5. 무료와 유료 두 가지 형태가 있다

  - MySQL 라이선스

    - MySQL은 두 가지 라이선스를 따른다.
      - 오픈 소스 라이선스(GPL)에 부합하는 한 무료로 사용 가능
      - 오픈 소스 라이선스(GPL)을 만족시키지 못하는 응용 프로그램을 배포할 생각이라면 별도의 상업용 라이선스를 사용

  

  #### 닷홈 무료 호스팅 신청

  [닷홈 무료 호스팅 신청](https://www.dothome.co.kr/web/free/index.php)

  1. 회원가입
  2. APM 공간 설치



### 2. FTP 클라이언트 프로그램 설치(Filezilla)

FTP란 File Transfer Protocol의 약자로 사용자 PC와 호스팅 서버 간의 파일을 송수신하는 프로그램을 의미한다. 파일이나 이미지 등 모두 서버로 업로드 되어야 웹이 동작하기 때문에 FTP 프로그램인 Filezilla client를 설치해준다. FTP 서버의 경우 이전에 신청했던 닷홈서버에서 이미 설치가 되어 있기 때문에 별도로 설치할 필요가 없다. 

[Filezilla client 설치](https://filezilla-project.org/)

[Filezilla client 사용 방법](https://www.dothome.co.kr/my/manual/hosting/11.php)



![dothome](assets/images/Filezilla.png)









### 3. 웹 에디터 설치

#### 1. 웹 에디터로는 Visual Studio Code를 설치한다. 

자신의 컴퓨터 OS에 맞는 버전의 VScode를 설치한다. 

[Visual Studio Code 설치](https://code.visualstudio.com/download)



#### 2. 인코딩 설정

에디터의 인코딩을 Utf-8로 설정한다. 



#### 3. VS code Extension 설치

- HTML Snippets extension
  - HTML 태그의 자동 완성 기능을 제공한다
- Sftp extension
  - 로컬에서 웹페이지를 만들고 ftp 클라이언트를 이용하여 업로드 하는 과정 없이 VS code 내에서 ftp 설정 후 편집하는 즉시 ftp를 이용해서 업로드 할 수 있는 기능을 제공한다. 

#### 4. 작업폴더 생성



#### 5. index.html 파일 작성 및 업로드



