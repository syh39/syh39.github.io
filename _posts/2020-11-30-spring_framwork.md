---
title:  "Spring Framework"
excerpt: "Framework는 애플리케이션 개발에 바탕이 되는 템플릿과 같은 역할을 하는 클래스들과 인터페이스, 라이브러리의 집합이라고 할 수 있다. "

categories:
  - Spring
tags:
  - Web
  - Spring
  - Framework
  - MVC
last_modified_at: 2020-11-30 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

---
## Framework

Framework는 애플리케이션 개발에 바탕이 되는 템플릿과 같은 역할을 하는 클래스들과 인터페이스, 라이브러리의 집합이라고 할 수 있다. 

라이브러리는 프로그램 제작시 필요한 기능들로 반복적인 코드 작성을 없애기 위해 언제든지 필요한 곳에서 호출되어 사용될 수 있도록 Class나 Function들로 이루어져있다. 라이브러리를 사용하면 필요한 로직을 직접 구현할 필요가 없이 라이브러리에서 제공하는 API를 호출하기만 하고 원하는 기능을 사용할 수 있게 되기 때문에 개발이 매우 편해진다. 

- 라이브러리 예시

  > - 자바스크립트의 jQuery
  > - Window에서 간혹 보이는 .dll(Dynamic-Link Library) 확장자 파일
  > - C표준 라이브러리

Framework에서 'Frame'은 사전적 의미로 '틀', '뼈대'라는 의미를 지니고 있다. 'Framework'라는 단어도 사전적 의미로 동일한 의미를 지니고 있다. 따라서 프레임워크는 '일정하게 짜여진 틀, 뼈대를 가지고 일한다' 라는 의미로 이해할 수 있다. 즉, 개발을 위해 필요한 기본적인 틀은 만들어져 있지만 기능 추가를 해주어야 하고 프레임워크가 정의한 규칙을 준수해야 한다. 개발자는 프레임워크를 사용함으로서 프레임워크가 제공해주는 기본적인 설계 기반 코드와 라이브러리들 위에서 하고 싶은 기능 구현에만 집중할 수 있게 된다. 즉, 틀은 다 짜여져 있고 내가 그 안을 채워 나가는 개념이다. 프레임워크는 개발자가 구현하고자 하는 기능을 쉽게 제공해줄 수 있다는 점에서 라이브러리와 공통점이 있다고 할 수 있다. 



## Spring Framework

Spring 프레임워크는 ''자바 엔터프라이즈 개발을 편하게 해주는 오픈소스 경량급 애플리케이션 프레임워크''라고 정의할 수 있다.   '애플리케이션 프레임워크'는 애플리케이션 개발의 전 과정을 빠르고 편리하며 효율적으로 진행하는데 일차적인 목표를 두는 프레임워크이다. 스프링이 '경량급'이라고 불리는 이유는 가장 단순한 환경인 Tomcat이나 Jetty에서도 완벽하게 동작하기 때문이다. 그런 면에서 단순한 개발환경만으로도 엔터프라이즈 개발에서 필요로 하는 주요한 기능을 갖춘, 비교적 애플리케이션을 쉽게 개발할 수 있는 프레임워크라고 할 수 있다. 참고로 'Spring'이란 이름의 의미는 개발자들에게 “개발의 겨울은 끝났다, 봄이 왔다” 라는 메세지를 준다는 의미로 지어진 이름이라고 한다. 스프링에서 개발을 더 쉽게 해주는 기술들은 다음과 같다. 

### 1. IoC(Inversion of Control, 제어의 역전)

기존의 개발자는 Java로 개발 시 new 연산자, 인터페이스 호출, 데이터 클래스 호출 방식으로 객체를 생성하고 소멸시켜야 했다. 하지만 스프링은 IoC를 제공함으로써 객체의 생성부터 소멸까지 객체의 생명주기 관리를 스프링 컨테이너에서 대신 해주게 된다. 프로그램이 커질 수록 객체와 자원을 이용하는 방식이 더 복잡해지기 때문에 코드가 꼬일 수도 있고 개발자가 실수할 수 있는 영역이 늘어나게 되는데 스프링이 이런 부분을 줄여주게 된다.

즉, 스프링 프레임워크에 맞춰서 개발해놓으면 스프링이 알아서 제어한다. 전체 웹 사이트의 제어권은 개발자에게 있는 것이 아닌 Spring에게 있다는 것이다. 그렇기 때문에 Spring이 알아서 제어를 할 수 있도록 우리가 특정 위치에 필요한 Controller, DAO, VO 등을 만들면 된다. 

### 2. DI(Dependency Injection, 의존성 주입)

프로그램에서 구성요소 간의 의존관계가 소스코드 내부가 아닌 외부의 설정파일을 통해 정의되는 방식이다. 이러한 방식을 통해 코드의 재사용성을 높여 다양한 곳에 사용할 수 있고 모듈간의 결합도도 낮출 수 있다. 쉽게 예를 들면 하나의 게임 캐릭터라는 객체가 존재하는데 그 객체를 더 잘 이용하기 위해 무기와 방패등 아이템을 가져와 결합시키는 것이다. 이 캐릭터 객체는 무기와 방패를 꼈다 뺐다를 자유자재로 할 수 있고 아이템을 갈아 끼우는데에 어떠한 구애를 받지 않는다. Java에서 데이터를 저장하고 가져오는 기능은 외부의 Oracle Database를 사용할 수도 있고 JDBC, iBatis, JPA등 다른 여러 프레임워크를 이용해 만들 수도 있다. 이때 스프링을 이용하면 그때마다 필요한 부분을 꼈다 뺐다 하면서 적절한 상황에 필요한 기능을 이용할 수 있다. 

### 3. AOP(Aspect Object Programming, 관점 지향 프로그래밍)

트랜잭션이나 로깅, 보안과 같이 여러 묘듈에서 공통적으로 사용하는 기능의 경우 해당 기능을 분리하여 관리할 수있다. 예를 들어 각각의 클래스가 있다고 가정하고 각 클래스들이 서로의 코드와 기능들이 중복되는 부분이 많다고 가정했을 때 코드가 중복될 경우 실용성과 가독성 및 개발 속도에 좋지 않을 것이다. 따라서 중복된 기능들을 전부 빼놓은 뒤 그 기능이 필요할 때만 호출하여서 쓰게 되면 효율성이 더 좋아질 것이다. 즉, AOP는 여러 객체에 공통으로 적용할 수 있는 기능을 구분함으로써 재사용성을 높여주는 프로그래밍 기법이다. 

### 4. POJO(Plain Old Java Object) 방식

'POJO'는 기존에 Java EE를 사용하면서 해당 플랫폼에 종속되어 있는 무거은 객체들을 만드는 것에 반발하여 나타난 용어이다. 스프링에서는 별도의 프레임워크 없이 Java EE를 사용할 때에 비해 인터페이스를 직접 구현하거나 상속받을 필요가 없어 기존 라이브러리를 지원하기 용이하고 객체가 가볍다. 즉, getter와 setter를 가진 단순한 자바 오브젝트를 의미한다. 

### 5. MVC 패턴***

웹사이트가 거대해지면서 요소와 기능들이 많아지고 구조가 복잡해짐에 따라 코드를 특정 기준으로 분리, 모듈화 해서 접근하게 되는데 MVC는 Model, View, Controller의 약자로 웹의 기능을 크게 3가지로 분리해 동적 웹페이지를 구현하는 패턴 중 하나이다.  Model은 웹사이트의 데이터의 형식을 지정하고 저장하고 불러 오는 등의 모든 데이터와 관련된 역할을 담당하고, View는 말 그대로 HTML과 CSS로 눈에 보여지는 페이지들을 의미하고, Controller는 Model과 View를 연결해서 사용자가 브라우저에서 데이터를 읽고 쓰고 지우는 것이 가능하도록 전반적 제어를 담당한다. 식당에 비유를 하자면 Model은 식료품 창고를 관리하고 음식을 요리하는 주방장에, View는 주방장이 만든 음식을 플레이팅하는 직원에, Controller는 주문을 받고 서빙을 하는 사람에게 음식을 전달해주는 매니저에 비유할 수 있다. 

MVC패턴을 보통 Model2라고 하기도 한다. 그 이유는 MVC패턴을 적용하기 이전에 사용하던 방식이 M,V,C가 분리되어 있지 않았었던 모델이기 때문이다. 때문에 기존의 모델을 Model1이라고 하고 MVC패턴이 적용된 모델을 Model2라고 부르게 되었다. 

#### Model1**

<center><img src="https://static.javatpoint.com/images/st/model1.jpg"></center>

- 기능적 분리 x
  1. 브라우저가 JSP 페이지에 대한 요청을 보낸다.
  2. JSP가 Java Bean에 접근해서 비즈니스 로직을 호출한다.
  3. Java Bean이 DB에 연결해서 데이터를 저장하거나 가져온다. 
  4. JSP에 의해 만들어진 응답이 다시 html형태로 브라우저로 반환된다. 

- 장점
  - 쉽고 빠르다
- 단점
  - 모든 페이지 사용자에게 노출 -> 보안 취약
  - 업무적으로 분리 X -> 협업 시 기능 다 이해하고 있어야 하고 순서에 따라 개발해야 함



#### Model2(MVC)**

![mvc](/assets/images/Spring/Spring_Framework/1.jpg)

<center><img src="https://howtodoinjava.com/wp-content/uploads/2015/02/Spring-dispatcher-servlet.png"></center>

> Spring Framework의 큰 틀

<center><img src="https://static.javatpoint.com/images/st/model2.jpg"></center>

<center><img src="https://howtodoinjava.com/wp-content/uploads/2015/02/mvc-architecture.gif"></center>



**그림 설명**

1. 일단 Controller가 모든 요청 받는다

2. 주소(URL)에 해당하는 모델 찾아서 기능 수행

3. 해당하는 데이터를 보여줄 View를 찾는다. 

   (Controller 파일 들어가면 다 명시되어있음)

- **Model**
  
  - **DB 작업**
  -  일반적으로 POJO로 구성된다.
  - Java Beans
  
- **View**
  
  - **사용자가 보는 페이지**
  - Model data의 렌더링(컨텐츠를 가져와서 구성)을 담당하며, HTML ouput을 생성한다.
  - JSP
  
- **Controller**
  
  - **View와 Model 사이의 인터페이스(컨트롤) 역할을 담당한다**
  - 사용자 요청을 수신하여 그에 따라 적절한 결과를 Model에 담아 View에 전달한다.
  - 즉, Model Object와 이 Model을 화면에 출력할 View Name을 반환한다.
  - Controller —> Service —> Dao —> DB
  - Servlet
  
  ~~~java
  package com.lab17.myap;
  
  import java.text.DateFormat;
  import java.util.Date;
  import java.util.Locale;
  
  import org.slf4j.Logger;
  import org.slf4j.LoggerFactory;
  import org.springframework.stereotype.Controller;
  import org.springframework.ui.Model;
  import org.springframework.web.bind.annotation.RequestMapping;
  import org.springframework.web.bind.annotation.RequestMethod;
  
  /**
   * Handles requests for the application home page.
   */
  @Controller
  public class HomeController {
  	
  	private static final Logger logger = LoggerFactory.getLogger(HomeController.class);
  	
  	/**
  	 * Simply selects the home view to render by returning its name.
  	 */
  	@RequestMapping(value = "/", method = RequestMethod.GET) // '/'url이 오면 아래 함수 내용을 실행해라
  	public String home(Locale locale, Model model) {
  		logger.info("Welcome home! The client locale is {}.", locale);
  		
  		Date date = new Date();
  		DateFormat dateFormat = DateFormat.getDateTimeInstance(DateFormat.LONG, DateFormat.LONG, locale);
  		
  		String formattedDate = dateFormat.format(date); // format을 이용해서 문자열로 변환
  		
  		model.addAttribute("serverTime", formattedDate ); // serverTime이라는 변수에 날짜 데이터를 저장 -> jsp 페이지로 데이터를 내보낼 때 이렇게 사용한다 / 모델(데이터)를 만든다.
  		
  		return "home";  // home.jsp를 실행해라
  	}
  }
  
  // 만약에 Controller에 등록된 페이지가 아니라면 jsp파일을 만들어도 의미 없다.(브라우저에서 보여지지 않는다)
  ~~~
  
  
  
- DispatcherServlet
  - Spring Framework가 제공하는 Servlet 클래스
  - 사용자의 요청을 받는다.
  - Dispatcher가 받은 요청은 HandlerMapping으로 넘어간다.
  
- HandlerMapping
  - 사용자의 요청을 처리할 Controller를 찾는다. (Controller URL Mapping)
  - 요청 url에 해당하는 Controller 정보를 저장하는 table을 가진다.
  - 즉, 클래스에 @RequestMapping(“/url”) annotaion을 명시하면 해당 URL에 대한 요청이 들어왔을 때 table에 저장된 정보에 따라 해당 클래스 또는 메서드에 Mapping한다.
  
- ViewResolver
  - Controller가 반환한 View Name(the logical names)에 prefix, suffix를 적용하여 View Object(the physical view files)를 반환한다.
  - 예를 들어 
    - view name: home, 
    - prefix: /WEB-INF/views/, 
    - suffix: .jsp는 
    - “/WEB-INF/views/home.jsp”라는 위치의 View(JSP)에 Controller에게 받은 Model을 전달한다.
  - 이 후에 해당 View에서 이 Model data를 이용하여 적절한 페이지를 만들어 사용자에게 보여준다.



- 장점
  - **Navigation control is centralized** - 컨트롤러가 페이지들을 결정하는 모든 로직을 가지고 있다. 
  - 유지보수가 쉽다
  - 확장성이 좋다
  - 테스트 하기 용이하다
- 단점
  - 컨트롤러 코드를 직접 써야 한다. 컨트롤러가 수정되면 다시 컴파일해서 다시 deploy 해야 한다. 



### Spring Framework vs Spring Boot

Spring Framework는 경량 컨테이너, IOC, DI, AOP등의 강력한 장점으로 인해 대표적인 자바 기반의 프레임워크로 자리잡았다. 하지만 많은 기능을 제공하는 만큼 설정하는데에 많은 시간을 써야 했다. Spring Boot는 그러한 Spring Framework의 단점을 커버하기 위해 나오게 되었다. Spring Boot의 장점은 다음과 같다. 

1. Tomcat이 내장되어 있다. 따로 설치하거나 매번 버전을 관리해줘야 할 필요가 없다. 
2. starter를 통한 dependency 자동화 -> 기존의 Spring에서는 dependency들 끼리 버전에 따라 영향을 미치는 경우가 있어서 버전 관리에 어려움이 있었다. 하지만 Spring boot에서는 starter가 대부분의 dependncy를 자동으로 관리해주기 때문에 훨씬 더 편해졌다. 
3. XML 설정을 안해도 된다. 
4. Jar file을 이용해 자바 옵션만으로 손쉽게 배포가 가능하다. 

Spring Boot가 이러한 기능들로 인해 Spring보다 더 간편해졌지만 그럼에도 불구하고 보통 Spring부터 배우기 시작하는 이유는 Spring을 배우면 Spring Boot는 쉽게 터득할 수 있지만 Spring Boot부터 배우면 Spring을 배우는데 시간이 걸리기 때문이다. 



### Spring Framework Project Structure

![mvc](/assets/images/Spring/Spring_Framework/2.jpg)



- src
  - 개발자가 작성한 Servlet 코드가 저장된다.
  - Controller, Model, Service, Dao
  - src/main/java
    - 개발되는 Java 코드의 경로
  - src/main/resources
    - 서버가 실행될 때 필요한 파일들의 경로
  - src/test/java
    - 테스트 전용 경로 (각 테스트 코드 작성 경로)
    - 단위테스트(Junit) - 내가 작성한 함수나 기능들이 잘 돌고 있는지 확인하는 기능 <!-- 회사에서 쓸 줄 아는지 확인하는 경우도 있다. -->
  - src/test/resource
    - 단위테스트 시 필요한 리소스들이 위치
- Libraries
  - Servlet이나 JSP에서 추가로 사용하는 라이브러리 또는 드라이버
  - jar로 압축한 파일이어야 한다.
- WebContent (전체 ROOT) - webapp
  - Deploy할 때 WebContent 디렉터리 전체가 .war로 묶어서 보내진다.
  - resources
    - 정적인 데이터 (ex. image file, css, js, fonts)
  - WEB-INF
    - 이 폴더 안에 있는 파일들은 브라우저에서 접근이 안된다. (보안 향상됨)
    - classes: 작성한 Java Servlet 파일이 나중에 .class로 이곳에 모두 저장된다.
    - lib: 추가한 모든 라이브러리 또는 드라이버가 이곳에 모두 저장된다.
    - props: property file을 저장한다.
    - spring: spring configuration files을 저장한다. (Spring과 관련된 설정 파일을 모아둔 것)
      - dispatcher-servlet.xml
      - applicationContext.xml
      - dao-context.xml, service-context.xml등
    - views: Controller와 매핑되는 .jsp 파일들을 저장한다. (JSP 파일의 경로)
    - **web.xml:** web application의 설정을 위한 web deployment descriptor
      - DispatcherServlet, ContextLoadListener 설정
      - **톰캣이 부르는 파일(해당 프로젝트를 동작시키기 위한 기본 설정 파일)**
        - 디폴트로 **servlet-context.xml** (servlet(view)과 관련된 것 - annotation 쓸지 말지, 톰캣이 해석할 필요가 없는 resource들 경로 설정, view resolver 세팅, base-package 설정 등)**과 root-context.xml** (비즈니스 로직과 관련된 것 - DB에 접속하는 Bean을 여기에 만들게 됨)**두개의 파일을 부른다**
- target 폴더
  - deploy할 war파일이 들어가는 폴더
- pom.xml
  - maven configuration file
  - 어떤 lib를 쓸지 명시한다.



### 기타

**패키지**

com.mycom.myapp 

- 이런 패키지가 있다면 보통 mycom에 해당하는 부분은 회사를 구분하는용이고 myapp에 해당하는 부분은 'context name'이라고 하는데 프로젝트(웹사이트)를 구분하는 용이다. (한 회사에서 여러 프로젝트(웹사이트)를 만들 수 있기 때문에)

- 패키지는 보통 기능별로(혹은 게시판 별로) 또 Controller / VO / DAO / Service로 나눠서 만든다
  - Controller
  - VO는 
  - DAO는 DB에 접속하는 로직
  - Service는 가져온 데이터들을 가공하는 작업
- 만약에 heroku에 deploy 했을 때 500에러(`500 error : java.lang.UnsupportedClassVersionError: com/mycom/myapp/HomeController has been compiled by a more recent version of the Java Runtime (class file version 58.0)`)가 뜨면 heroku보다 자바버전이 더 높아서 생긴 문제이다. 이 경우 Java Build Path에서 자바 버전을 14로 바꾸고 루트 디렉토리에 `system.properties` 파일을 만들고 `java.runtime.version=14`라는 내용을 넣고 다시 maven install 후 deploy 하면 된다. deploy할 때는 `heroku war:deploy [이름].war system.properties --app [앱이름] ` 으로 하면 된다. (수정한 자바 버전이 14가 아니어도 상관없다)



### 출처

- <https://howtodoinjava.com/spring-mvc/spring-mvc-hello-world-example/>
- <https://www.javatpoint.com/model-1-and-model-2-mvc-architecture>