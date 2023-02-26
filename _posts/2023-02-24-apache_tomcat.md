---
title:  "Apache Tomcat 정리"
excerpt: "아파치 톰캣을 안다고 생각했지만 웹 서버라는 정도만 애매하게 알고있어서 이 기회에 제대로 알고자 정리해보았다. "

categories:
  - Web
tags:
  - Apache
  - Tomcat
  - Spring
last_modified_at: 2023-02-24 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

---

### Apache Tomcat 이란

![image](https://user-images.githubusercontent.com/54565079/221055666-3f12ba47-bf6a-4e71-86b1-238cdbaa353f.png)

아파치 톰캣을 안다고 생각했지만 웹 서버라는 정도만 애매하게 알고있어서 이 기회에 제대로 알고자 정리해보았다. 



### Apache

- [아파치](https://www.apache.org/)는 **소프트웨어 재단**임과 동시에 아파치 소프트웨어 재단에서 만든 **HTTP 웹서버 이름**이기도 하다. 그래서 사람들이 많이 헷갈리지 않나 생각한다. 
- 오픈소스이고 무료인데 기능이 많고 구축이 쉬워서 많이 쓰이고 있다. 
- 80 포트를 사용한다
- 정적 웹서버이다. 
  - 정적 웹 서버란
    - 이미지나 단순 html 파일들을 처리하는 서버
    - 모든 사람이 동일한 화면을 보게 되는 경우에 정적 웹서버를 주로 사용
    - 현재 깃허브 블로그도 정적 웹서버의 한 예시



### Tomcat

- [톰캣](https://tomcat.apache.org/)은 아파치 소프트웨어 재단에서 만든 WAS(Web Application Server)이다. 
- 웹 서버와 연동하여 실행할 수 있는 자바 환경을 제공
- Web.xml 파일을 통해 필요한 설정 가능
- 8080 포트를 사용한다.
- 톰캣은 아파치 웹 서버와 따로 존재할 수 있지만 일반적으로 아파치 웹 서버를 내장하고 있기 때문에 웹 서버 + 웹 컨테이너(Servlet 컨테이너라고도 부름)의 결합으로 정적인 데이터에 더해 동적인 데이터도 처리할 수 있다 -> 동적 웹서버이다. 
  - 동적 웹 서버란
    - DB와 연결되어 데이터를 주고 받거나 코드로 데이터 조작이 필요한 경우에 사용하는 서버
  - Servlet이란
    - WAS에서 HttpServlet을 상속 받은 Java 클래스로  동적인 처리를 담당하는 역할
- '아파치 톰캣' 이라고 부르는 이유는 톰캣도 아파치 재단에서 만들었기 때문에 그렇게 부르기도 하지만  ~~(현대 싼다페 처럼)~~ 톰캣 내에 아파치 웹서버가 있기 때문에 그렇게 부르기도 한다. ~~다시 한번 말하지만 아파치 톰캣이 헷갈리는 이유는 재단 이름이 아파치인데 걔네가 만든 서버 이름도 아파치인게 가장 큰 이유이고 적폐이다.~~
- 그림으로 보면 이런 식이다![image](https://user-images.githubusercontent.com/54565079/221062204-1e30c191-7416-497b-8cb3-b5adeda1a8e2.png)
- 단순 정적 데이터는 웹서버에서 정적 데이터를 바로 리턴하지만 동적 데이터(JSP, PHP 등의 페이지나 DB 연결, 데이터 조작, 다른 응용 프로그램과 상호 작용 등)는 웹 컨테이너를 통해 처리하고 정적인 파일로 만들어진 결과물을 리턴하게 된다. 



### Apache vs Tomcat

- 아파치는 단순 웹서버이고 톰캣은 WAS이다. 둘의 차이는 컨테이너(동적 처리) 기능이다. 
- 필요에 따라 아파치만 쓰는게 더 성능이 좋을 수도 있다. 



### 출처

- <https://cheershennah.tistory.com/54>
- <https://kchanguk.tistory.com/2>
- <https://jaehoney.tistory.com/38>
- <https://melonicedlatte.com/2020/07/08/231200.html>
- <https://velog.io/@kdhyo/Apache-Tomcat-%EB%91%98%EC%9D%B4-%EB%AC%B4%EC%8A%A8-%EC%B0%A8%EC%9D%B4%EC%A7%80>
- <https://velog.io/@welchs1423/%EC%95%84%ED%8C%8C%EC%B9%98-%ED%86%B0%EC%BA%A3>
- <https://hoon-k.tistory.com/5>

