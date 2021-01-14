---
title:  "Javascript AJAX"
excerpt: "AJAX는 **A**synchronous **J**avaScript **A**nd **X**ML의 약자이다."

categories:
  - Web
tags:
  - Web
  - AJAX
last_modified_at: 2021-01-13 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---



### AJAX*

AJAX는 **A**synchronous **J**avaScript **A**nd **X**ML의 약자로 자바스크립트와 XML로 비동기식 작업을 하는 것을 의미한다. 'Asynchronous'는 비동기라는 뜻으로 어떤 일을 하고 있는 상태에서 백그라운드(자바스크립트)에서 자동으로 다른 일을 할 수 있는 것을 의미한다. 동기식 작업은 반대로 순차적으로 어떤 일이 종료 되고 나서 다음 일이 진행되는 방식을 의미한다. 예를 들어 웹 페이지를 열 때 url 을 입력하면 서버에서 그 요청을 받아서 클라이언트에게 주면 그 응답을 받아서 웹 페이지를 띄워주는 방식이 동기식 작업이다. 로그인 과정도 마찬가지로 로그인 정보를 입력하면 서버에서 로그인 정보를 확인하고 확인이 되면 로그인 된 화면이 나오도록 하는 것도 동기식 작업이다. 

따라서 AJAX는 프로그래밍 언어가 아닌 개념을 의미하게 된다.  AJAX는 `XMLHttpRequest`객체와 자바스크립트 + HTML DOM의 조합을 사용한다. AJAX는 개발자의 이상을 실현시켜준다고 말할 수 있는데 그 이유는 현재 페이지를 새로고침하지 않은 상태로 웹 서버로부터 데이터를 읽어서 현재 페이지에 내용을 띄워주거나 다시 서버로 데이터를 보낼 수 있기 때문이다. AJAX가 실행되는 큰 그림을 보면 다음과 같다. 

![Ajax](https://www.w3schools.com/js/pic_ajax.gif)

1. An event occurs in a web page (the page is loaded, a button is clicked)
2. An XMLHttpRequest object is created by JavaScript
3. The XMLHttpRequest object sends a request to a web server
4. The server processes the request
5. The server sends a response back to the web page
6. The response is read by JavaScript
7. Proper action (like page update) is performed by JavaScript



### XMLHttpRequest Object

AJAX의 핵심은  `XMLHttpRequest` 객체이다. 모든 브라우저들은 `XMLHttpRequest` 를 지원하는데 `XMLHttpRequest` 객체는 웹 서버와 데이터를 주고 받게 해준다. 즉, 이 객체를 통해 웹 페이지를 새로고침하지 않고 웹 페이지의 특정 부분만 업데이트를 하는게 가능해진다. 

**AJAX 예시 코드**

~~~html
<!DOCTYPE html>
<html>
<body>

<div id="demo">
<h2>The XMLHttpRequest Object</h2>
<button type="button" onclick="loadDoc()">Change Content</button>
</div>

<script>
function loadDoc() {
  var xhttp = new XMLHttpRequest();   // 1. XMLHttpRequest 객체를 만든다. 
  xhttp.onreadystatechange = function() { // 3. XMLHttpRequest 객체의 상태가 변경되었을 때 (GET방식으로 가져왔을 때 / 이벤트)
    if (this.readyState == 4 && this.status == 200) { // 4. readyState==4(request finished and response is ready) / status==200(OK / 그 파일 있다) 이 두가지가 확인 되면
      document.getElementById("demo").innerHTML =
      this.responseText;  // 5. id==demo 인 곳에 받아온 데이터를 넣어라
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);  // 2. GET 방식으로 이 파일을 호출해라 (XMLHttpRequest 객체를 이용하여) / 구현해보려면 일단 서버쪽에 파일 하나 만들어놓고 GET(혹은 POST) 방식으로 가져오면 된다. 
  xhttp.send();
}
  
</script>

</body>
</html>
~~~

[연습 링크](https://www.w3schools.com/js/tryit.asp?filename=tryjs_ajax_first)



### Server Response

| 구분               | 설명                                                         |
| ------------------ | :----------------------------------------------------------- |
| onreadystatechange | Defines a function to be called when the readyState property changes |
| readyState         | Holds the status of the XMLHttpRequest. 0: request not initialized / 1: server connection established / 2: request received / 3: processing request / 4: request finished and response is ready |
| status             | 200: "OK"  / 403: "Forbidden" / 404: "Page not found" / For a complete list go to the [Http Messages Reference](https://www.w3schools.com/tags/ref_httpmessages.asp) |



### AJAX의 유용성

AJAX의 장점은 개발자의 컨텐츠가 전부 노출이 되지 않는다는 것이다. 내부적으로 자바스크립트를 이용해서 다 요청하게 되어있다. (요즘에는 크롬이 개발자도구를 잘 만들어놔서 다 노출되긴 한다)

AJAX는 현재 페이지에서 필요한 내용 때문에 페이지를 왔다 갔다 할 필요 없이 클릭을 하면 특정 영역 안에 필요한 정보만 그때마다 가져와서 보여줄 수 있기 때문에 매우 유용한 기술이다. 위의 예시 코드는 vanilla.js(순수 자바스크립트로 만드는 방법)이고 jQuery 라이브러리로 더 간단하게 만들 수 있다. <!-- (카카오 채용에선 자바스크립트로 아작스 구현할 줄 알아야 한다고 되어 있음) -->