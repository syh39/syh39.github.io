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

#### Heroku 가입 및 세팅

1. heroku 가입 : [www.heroku.com/](https://www.heroku.com/)

2. Heroku Command Line Interface (CLI)  설치  - > deploy 할 때 터미널 명령어로 한다
   <https://devcenter.heroku.com/articles/heroku-cli>
    mac : <https://whitepaek.tistory.com/3>
           <https://nhj12311.tistory.com/28>

3. 설치 확인
   heroku --version

   ![스크린샷 2021-01-23 오후 11.17.38](/assets/images/jsp_project/38.png)

   heroku login
   \* heroku login > 브라우저에서 로그인 클릭 > 다시 재입력

   <center><img height="400" src="/assets/images/jsp_project/59.png"></center>

   

#### STS4에서 새 프로젝트 만들기

1. dynamic web project 생성

2. maven project로 변경

    [정리 링크](https://syh39.github.io/web/Spring_git/#%EC%83%88-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0)

3. index.jsp 생성 및 실행

4. heroku 사이트에 들어가서 새로운 app생성

   <https://dashboard.heroku.com/apps>

   ![스크린샷 2021-01-23 오후 11.21.58](/assets/images/jsp_project/58.png)

5. deploy : terminal 작업

   - heroku plugins:install java[enter]

   - mvn package (프로젝트 폴더내에서)
     에러발생시 pom.xml 수정
      <plugin>
      <artifactId>maven-war-plugin</artifactId>
      <version>2.4</version>
      <configuration>
      <warSourceDirectory>WebContent</warSourceDirectory>
      <failOnMissingWebXml>false</failOnMissingWebXml>
      </configuration>
     </plugin>

     수정 후 maven > update project 할것

   - sts4에서 배포판 만들기 : run > maven install -> war 패키지 생성

   - heroku war:deploy heroku-0.0.1-SNAPSHOT.war --app second1004
     heroku-0.0.1-SNAPSHOT.war : 프로젝트 target 에 만들어짐
     app 이름은 heroku 앱 이름 

6. 주소실행(heroku에서 앱 열기해도 됨)

7. jdk version 오류로 인행 에러날 때

   - heroku war:deploy CRUDProject-0.0.1-SNAPSHOT.war system.properties --app hgu1004
   - system.properties
     - java.runtime.version=14

