---

title: "Spring Controller Method"
excerpt: "Controller는 MVC패턴에서 URL요청을 처리한 후에 지정된 뷰에 모델 객체를 넘겨주는 역할을 하는 뷰와 모델의 인터페이스이다. " 

categories:
  - Spring
tags:
  - Web
  - Java
  - JSP
  - Spring

last_modified_at: 2021-01-27 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

<h3 style="color:navy">Controller란</h3>

Controller는 MVC패턴에서 URL요청을 처리한 후에 지정된 뷰에 모델 객체를 넘겨주는 역할을 하는 뷰와 모델의 인터페이스이다. Controller는 여러가지 파라미터와 리턴 타입을 갖는다. 

#### Controller Method Parameter

##### httpServletRequest.getParameter()

~~~java
@RequestMapping("/test") 
public String test(HttpServletRequest req) {

	String userId = req.getParameter("userId");
	return "test"; 
}
~~~

getParameter()는 String 값을 반환한다.



##### httpServletRequest.getAttribute()

~~~java
@RequestMapping("/test") 
public String test(HttpServletRequest req) {

	String userId = req.getAttribute("userId");
	return "test"; 
}
~~~

getAttribute()는 getParameter()와 비슷하지만 String 값이 아닌 Object 값을 반환한다는 차이가 있다.



##### @RequestParam

~~~java
@RequestMapping("/test", method=RequestMethod.GET)
public String test(@RequestParam(value="userId", defaultValue="ooeunz") String userId) {

	return "test"; 
}
~~~

@RequestParam은 query string 방식으로 url을 통해 parameter로 값을 받아온다. 갖고있는 속성으로는 value, required, defaultValue가 있다.

- value는 위의 코드에서 알 수 있듯이 query string으로 받아오는 key값을 의미하고 뒤에 오는 변수에 해당 값을 바인딩한다.
- required값은 true일 경우 parameter가 반드시 url에 담겨있어야 한다. 없을경우 400값을 반환하게 된다.
- defaultValue는 디폴트 값을 의미한다.

※ Query String 방식과 path value 방식이 무엇인지 모른다면 아래 url을 참고하자.

<https://ooeunz.tistory.com/43?category=849959>

<!-- 이 부분 다시 공부하자 -->

##### @PathVariable

~~~java
@RequestMapping("/test/{email}", method=RequestMethod.GET)
public String test(@PathVariable("email") String email) {

	return "test"; 
}
~~~

@Pathvariable 어노테이션은 RequestMapping에 {email} 이라는 부분에 맵핑된다. query string 방식과 path value 방식을 이해하고 있다면 별로 어렵지 않게 사용할 수 있다.



##### @RequestBody

~~~java
@RequestMapping("/test")
public String test(@RequestBody Map<String, Obejct> obj) {
	Account account = obj.get("account"); 
	return "test"; 
}
~~~

GET방식은 request packet에 http body가 존재하지 않는다. 따라서 @RequestBody로받으려면 반드시 POST 방식을 사용해야 한다. @RequestBody는 JSON이나 XML과 같은 데이터를 받거나 DTO/VO 객체 전체를 받을 경우 사용한다.



##### @ModelAttribute

~~~java
@RequestMapping("/test")
public String test(@ModelAttribute UserDto user) {
	
    System.out.println(user.getUserId());
	return "test"; 
}
~~~

@RequestParam과 비슷한데 1:1로 parameter를 받을 경우엔 @RequestParam을 사용하고 DTO/VO와 같이 객체 전체로 받을 경우 @ModelAttribute로 받을 수 있다. 예를 들어 form에서 데이터를 받을 경우 form name과 DTO/VO의 변수 명을 같게 해줌으로써 자동으로 데이터를 바인딩할 수 있다.





#### Controller Method Return Type

##### ModelAndView

~~~java
@Controller 
public class HelloController {

  @RequestMapping("/hello") 
  public ModelAndView hello() { 
    ModelAndView view = new ModelAndView(); 
    
    // View는 hello.jsp 
    view.setViewName("hello"); 
    
    // [hello.jsp] ${name} = Lim 
    view.addObject("name", "Lim"); 
    
    return view; 
  } 
}
~~~

`http://localhost:8080/hello` 를 REQUEST한 경우, **hello.jsp**가 View가 된다.



##### String

~~~java
@Controller 
public class HelloController { 
  
  @RequestMapping("/hello") 
  public String hello() { 
    
    // View는 hello.jsp 
    return "hello"; 
  }
}
~~~

String의 경우 리턴 값이 View의 이름으로 사용된다.

`http://localhost:8080/hello` 를 REQUEST한 경우, **hello.jsp**가 View가 된다.



##### void

~~~java
@Controller 
public class HelloController { 
  
  @RequestMapping("/hello") 
  public void hello() { 
  } 
}
~~~

**RequestToViewNameResolver**를 통해 자동생성되는 View 이름이 사용된다.

URL과 View 이름을 통일하여 사용해야한다.



##### Object

**RequestToViewNameResolver**를 통해 자동생성되는 View 이름이 사용된다.



##### @ResponseBody

~~~java
@Controller 
public class HelloController { 
  
  @RequestMapping("/hello") 
  @ResponseBody
  public String hello() { 
    return "<html><body><h1>Hello, ResponseBody!</h1></body></html>"; 
  }

}
~~~

@ResponseBody가 메소드레벨에 부여되는 경우, 메소드가 리턴하는 오브젝트는 View를 통해 결과를 만들어 내는 모델로 사용되는 대신, 메시지 컨버터를 통해 바로 HTTP 응답의 메시지 본문으로 전환된다.

return 값이 단일 모델 오브젝트이고 메시지 컨버터가 View와 같은 방식으로 동작한다.





#### 출처

- <https://ooeunz.tistory.com/99>
- <https://sambalim.tistory.com/69>















