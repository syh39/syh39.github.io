---
title:  "Spring Framework 초기설정 및 Git 연동하기"
excerpt: "Spring Framework는 자바 플랫폼을 위한 오픈소스 애플리케이션 프레임워크로 동적 웹 사이트를 개발하기 위한 프레임워크이다." 

categories:
  - Web
tags:
  - Web
  - Java
  - Spring
  - Git
  - Framework
  - Tomcat
last_modified_at: 2021-01-18 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

### **Spring Framework**

Spring Framework는 자바 플랫폼을 위한 오픈소스 애플리케이션 프레임워크로 동적 웹 사이트를 개발하기 위한 프레임워크이다. 현재 우리나라 공공 기관의 웹 서비스 개발시 사용을 권장하고 있는 [전자정부 표준프레임워크](https://ko.wikipedia.org/wiki/전자정부_표준프레임워크)의 기반 기술로 쓰이고 있다. 

 

### JSP/Spring 개발을 위한 설치

스프링으로 웹 개발을 하기 위해 필요한 설치들은 다음과 같다. 

#### JDK 설치

- **JDK 8 이상**<https://www.oracle.com/java/technologies/javase-jdk14-downloads.html>
  - 자바를 사용하기 위해 JDK를 설치해준다.
  - 설치후 JAVA_HOME 과 path 설정 
  - 설치확인 : java -version

#### Tomcat 서버 설치

- STS 내에서 자바 코드를 해석할 수 있는 WAS 서버(웹 서버의 기능도 수행함) / 디플로이 전에 테스트 용도이다. 

- **Tomcat 8.5 이상** <https://tomcat.apache.org/download-80.cgi>

#### STS 설치(Eclipse 해도 된다)

- **Spring Tool Suite 4**

   (or Eclipse for JavaEE) <https://spring.io/tools>

  - 폰트 크기 변경 / encoding 변경
    - <https://m.blog.naver.com/PostView.nhn?blogId=reinstate10&logNo=220049800243&proxyReferer=https:%2F%2Fwww.google.com%2F>

#### Spring Add-on 설치

- **spring Tools 3 Add-On for Spring Tools 4.3.9.14 Release(Eclipse MarketPlace)**
  - 설치 후 Spring 프레임워크를 이용한 개발을 할 수 있다. 
- (설치안해도 됨)**Maven3** 이상 <http://maven.apache.org/download.cgi>
  - 설치후 path 설정
  - 설치확인 : mvn -version
  - maven은 필요한 라이브러리를 자동으로 관리 + 빌드 관리해준다. gradle이라는 것도 있지만 sts4는 기본적으로 maven 사용한다.
  - STS 4에서는 Maven이 포함되서 설치되기 때문에 별도로 설치할 필요가 없다. 
- 설치 참고 링크
  -  <https://m.blog.naver.com/PostView.nhn?blogId=rhrkdfus&logNo=221491244470&proxyReferer=https:%2F%2Fwww.google.com%2F>



위의 설치가 완료되면 기본적으로 STS + 터미널 + 브라우저로 개발을 하게 된다. 



### 새 프로젝트 만들기

- 순수 JSP 프로젝트 만들기(보통 이렇게 안하고 Spring 프로젝트를 만든다)

1. 파일탭이나 Project Explorer 빈 공간에 우클릭 후 New-Other-Dynamic Web Project(JSP를 이용한 기본 웹 프로젝트 / 안나오면 검색하면 됨)  - 프로젝트 이름 입력 - Target runtime에 Tomcat 지정 - Finish 

2. 라이브러리를 자동으로 관리해주는 Maven 프로젝트로 변환하기 위해 프로젝트 우클릭 - Configure - Convert to Maven Project - Finish 하게 되면 pom.xml 이 나오는데 이 파일은 현재 프로젝트와 관련된 정보들이 들어있다. 이 파일에 라이브러리를 설정할 수 있다. 

   

### Git 연동하기

1. Git 계정 로그인 
2. 저장소 새로 만들기(README 파일같은거 만들면 한번 pull 받아야 해서 귀찮아짐)
3. STS Window탭 - Show View - Other - git 검색/선택 - open - Clone a git repository - git URL/ID/PW 입 - next - next - Finish / 여기까지 하면 로컬의 깃 폴더와 리모트 깃폴더 연결 완료
4. 현재 프로젝트와 로컬의 깃 폴더를 연결하기 위해 프로젝트 우클릭 - Team - Share Project - 로컬 깃 프로젝트 Browse (맥 기준 보통 사용자 - git 폴더 안에 있음) - Finish / 여기까지 하면 Working Tree(로컬 깃 저장소)와 연결 완료
5. 깃으로 커밋 안할 파일들을 .gitignore 파일에 담기 위해 구글에 gitignore 검색 - 사이트에서 [운영체제, 언어, 에디터 등] 입력(이 경우 macOS, Java-Web, Eclipse, Maven 입력함 / 이렇게 하면 이런 환경에서 깃에서 추적하지 않아도 되는 파일들을 찾아준다) - 다른 이름으로 저장 - Working Tree 위에(첫번째 프로젝트 이름 폴더 / .git파일이 있는지 여부로 확인) .gitignore라고 저장 
6. 프로젝트 우클릭 - Team - Commit - +나 ++ 클릭 - 커밋 메세지 입력 - 푸쉬

- 팁 : Git Staging 탭을 항상 보이게 해놓으면 한눈에 staging, commit, push 상태를 다 확인할 수 있어서 편하다. 



### 프로젝트 페이지 테스트하기

WebContent폴더 우클릭 - New - HTML or JSP - 파일 이름 입력 - Finish - Hello World 작성 - 프로젝트 우클릭 - Run As - Run on Server(Tomcat) - Finish

