---

title:  "Spring Controller Method"
excerpt: "" 

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

### 

### Controller란

Controller는 MVC패턴에서 URL요청을 처리한 후에 지정된 뷰에 모델 객체를 넘겨주는 역할을 하는 뷰와 모델의 인터페이스이다. Controller는 여러가지 파라미터를 받을 수 있다. 

 #### HttpServletRequest.getParameter()

~~~java
@RequestMapping("/main.do") 
public String main(HttpServletRequest request) { 
  String id = request.getParameter("id"); 
  System.out.prinln(id); 
  return "main"; 
}
~~~

HttpServletRequest의 getParameter() 메서드를 이용하여 파라미터 값을 가져올 수 있다.

이때 parameter로 보낸 **변수명**과 getParameter("**변수명**") 에 들어갈 변수명이 일치해야한다.



#### **@RequestParam**

@RequestParam 어노테이션을 이용하여 파라미터값을 가져오는 방법이다.

| **이름**                     | **타입** | **설명**                               |
| ---------------------------- | -------- | -------------------------------------- |
| name, value (Alias for name) | String   | 파라미터 이름                          |
| required                     | bollean  | 해당 파라미터의 필수 여부, 기본값 true |
| defaultValue                 | String   | 해당 파라미터 기본값                   |

 위 옵션값들을 조합하여 컨트롤러 메서드에 적용하면 request 파라미터값을 가져올 수 있다. 가장 기본적으로는 파라미터 이름 value 옵션만으로도 사용 가능하다.

~~~java
@RequestMapping("/main.do") 
public String main(@RequestParam(value="id", defaultValue="haenny") String id){ 			  			System.out.prinln(id); 
	return "main"; 
}
~~~

