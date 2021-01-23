---

title:  "JSP 프로젝트 호스팅하기"
excerpt: "" 

categories:
  - Web
tags:
  - Web
  - Java
  - JSP

last_modified_at: 2021-01-22 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

### **JSP Project Hosting**

웹 서비스를 만든다는 것은 로컬에서 돌아가는 웹 서비스를 만드는 것이 아닌 모든 사람이 접속 할 수 있는 웹 서비스를 만드는 것이다. 따라서 웹 서비스를 인터넷을 통해 다수의 사람들이 접근해서 사용할 수 있도록 해야 한다. 그러기 위해서는 로컬에서 프로젝트 소스 작업을 마친 후에 인터넷 기반의 서버로 프로젝트를 디플로이(Deploy)해야 한다. 인터넷에 서버를 호스팅해주는 여러 사이트가 있는데 여기서는 Heroku라는 인터넷 서버(Paas)를 사용해 볼 것이다. 

#### 1. Heroku 가입 및 세팅

1. heroku 가입 : [www.heroku.com/](https://www.heroku.com/)

2. Heroku Command Line Interface (CLI)  설치  - > deploy 할 때 터미널 명령어로 한다
   <https://devcenter.heroku.com/articles/heroku-cli>
    mac : <https://whitepaek.tistory.com/3>
           <https://nhj12311.tistory.com/28>

3. 설치 확인
   heroku --version

   ![스크린샷 2021-01-23 오후 11.17.38](/assets/images/jsp_project/38.png)
   터미널에서 heroku login > 브라우저에서 로그인 클릭 > 다시 재입력

   <center><img height="400" src="/assets/images/jsp_project/59.png"></center>

   

#### 2. STS4에서 새 프로젝트 만들기

1. dynamic web project 생성

2. maven project로 변경

    [정리 링크](https://syh39.github.io/web/Spring_git/#%EC%83%88-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0)

3. 소스코드 생성 및 로컬 테스트

   1. DB table 생성

      > 예시

      ~~~sql
      create table BOARD ( 
      	seq int AUTO_INCREMENT,
        title varchar(100),
        writer varchar(100),
        content varchar(100),
        regdate timestamp default current_timestamp, cnt int default 0, 
        primary key(seq),
      )
      ~~~

      

   2. bean 생성

   3. CRUD 파일들 생성 (addform.html / add_ok.jsp / list.jsp / edit...etc)

   4. 로컬 테스트 

4. heroku 사이트에 들어가서 새로운 app생성

   <https://dashboard.heroku.com/apps>

   ![스크린샷 2021-01-23 오후 11.21.58](/assets/images/jsp_project/58.png)



#### 3. Deploy

1. deploy는 터미널로 작업한다(다른 방법도 있긴 하다).

2. heroku plugins:install java[enter]  -> heroku에 자바 설치됨

3. mvn package (프로젝트 폴더내에서)
   에러발생시 pom.xml 수정

   ~~~xml
    <plugin <plugin됨>
    <artifactId>maven-war-plugin</artifactId>
    <version>2.4</version>
    <configuration>
    <warSourceDirectory>WebContent</warSourceDirectory>
    <failOnMissingWebXml>false</failOnMissingWebXml>   <!-- 이 줄 추가 / heroku와 호환됨 -->
    </configuration>
   </plugin>
   ~~~

   수정 후 maven > update project 할것(pom.xml 파일에 맞춰서 maven 업데이트 됨)

   - (가끔 파일 추가나 삭제가 프로젝트에 제대로 반영이 안될 경우 위에 Project -> Clean 해주면 프로젝트가 전체적으로 Refresh 됨)
   - 여러명이서 협업할 때 버전이 안맞아서 문제가 생기는 경우
     -  Java Build Path에서 라이브러리 버전들 확인할 것
     -  Java Build Path - Java Compiler 버전 확인할 것
     -  Java Build Path - Project Facets 버전들 확인할 것

4. sts4에서 배포판 만들기 : Run  as -> maven install -> war 패키지(배포판) 생성

   > 성공 화면

   ![20](/assets/images/jsp_project/20.png)

   성공하면 target 폴더 내에 war 파일이 생성되는데 만약에 확인이 안되면 프로젝트 refresh 해주면 됨. 

   

   - 배포할 때는 프로젝트를 모두 서버에 올리는 것이 아닌 

     - 프론트엔드 페이지 소스코드들과
     - Jave Resources-src 아래의 패키지들(자바 클래스 파일들)을 모두 바이트 코드로 변환한 리소스들(소스코드x)과
     - xml 설정파일들

     을 모아서 압축해서 서버에 올리게 된다. 서버는 그 압축파일을 풀고 서비스를 하게 된다. 

5. 터미널에서 `heroku war:deploy [프로젝트이름]-0.0.1-SNAPSHOT.war --app [heroku 앱 이름]`  입력
   (target 폴더로 들어가서 [프로젝트]-0.0.1-SNAPSHOT.war 파일 이름 복사하기)

   1. 주소실행(heroku에서 앱 열기해도 됨 / `heroku open --app [heroku 앱 이름]`)

   - 로컬에선 잘 돌아가는데 deploy 이후에 에러가 나는 경우 대부분 JDK(자바 버전)문제이다. 그런 경우 터미널에서 deploy할 때 heroku의 자바 버전 확인할 수 있는데 현재 로컬 프로젝트의 자바 버전(Build Path -> Configure Build Path에서 확인 가능)과 맞는지 확인
   - 만약에 로컬에서도 에러가 난다면 코드 상의 문제이다. 에러 메세지 유심히 읽어서 디버깅 할 것.
     - `heroku war:deploy [프로젝트이름]-0.0.1-SNAPSHOT.war system.properties --app [heroku 앱 이름]`
     - system.properties
       - java.runtime.version=14

#### Github 업로드

Deploy가 성공하면 다른 사람들과의 협업을 위해 깃허브에 업로드한다. 