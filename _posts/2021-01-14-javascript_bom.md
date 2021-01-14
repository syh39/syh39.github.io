---
title:  "Javascript HTML BOM"
excerpt: "BOM(Browser Object Model 의 약자)은 브라우저에 대한 모든 내용을 담고있는 객체로 자바스크립트가 제어할 수 있도록 한 것이다."

categories:
  - Web
tags:
  - Web
  - BOM
last_modified_at: 2021-01-13 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

### HTML BOM

BOM(Brouser Object Model 의 약자)은 브라우저에 대한 모든 내용을 담고있는 객체로 자바스크립트가 제어할 수 있도록 한 것이다. 브라우저에 관련 된 내용(뒤로가기, 북마크, 즐겨찾기, 히스토리, URL정보 등..) 모두 담고있다. 즉, 브라우저가 가지고 있는 정보를 따로 객체화 시켜서 관리한다. 



### Window Object

`window`객체는 모든 브라우저에서 지원된다. `window`객체는 브라우저의 현재 창을 대표하게 되고 모든 자바스크립트의 글로벌 객체, 함수, 변수들은 전부 `window`객체의 멤버가 된다. 



### Screen

`window.screen` 객체는 사용자의 스크린에 대한 정보를 담고 있다.  `window.screen`객체는 `window`prefix 없이 사용가능하다. `screen`객체의 속성들은 다음과 같다. 

- `screen.width`
- `screen.height`
- `screen.availWidth`
- `screen.availHeight`
- `screen.colorDepth`
- `screen.pixelDepth`

[링크](https://www.w3schools.com/js/js_window_screen.asp)



### Location*

`window.location`객체는 브라우저의 위치와 관련된 기능이다. 현재 창에서 뒤로 가기, 앞으로 가기, 새로 고침, 특정 사이트로 이동 등이 가능하다. `window.location`객체도 마찬가지로  `window`prefix 없이 사용가능하다. `location`객체의 속성들은 다음과 같다. 

- `window.location.href` returns the href (URL) of the current page
- `window.location.hostname` returns the domain name of the web host
- `window.location.pathname` returns the path and filename of the current page
- `window.location.protocol` returns the web protocol used (http: or https:)
- `window.location.assign()` loads a new document

> assign = href(더 많이 쓴다)

~~~html
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript</h2>
<h3>The window.location object</h3>

<input type="button" value="w3school" onclick="newDoc()">
<button id=naver1>Go Naver</button>
  
<script>
function newDoc() {
  window.location.assign("https://www.w3schools.com")
}
document.getElementById("naver1").addEventListener("click", goNaver);
function goNaver() {
	location.href = "https://www.naver.com/";
}
</script>

</body>
</html>
~~~

[연습링크](https://www.w3schools.com/js/tryit.asp?filename=tryjs_loc_assign)

[링크](https://www.w3schools.com/js/js_window_location.asp)



### History*

`window.history` 객체는 브라우저의 히스토리를 가지고 있는 객체이다. `window.history`객체도 마찬가지로  `window`prefix 없이 사용가능하다. `history.back()` 과 `history.forward()`함수를 통해 히스토리 리스트의 이전 페이지나 다음 페이지로 갈 수 있다. 

[링크](https://www.w3schools.com/js/js_window_history.asp)



### Navigator

`window.navigator` 객체는 현재 접속하고 있는 브라우저에 대한 정보(explorer, chrome)를 가지고 있다. `window.navigator`객체도 마찬가지로  `window`prefix 없이 사용가능하다. 

- `navigator.appName`
- `navigator.appCodeName`
- `navigator.platform`

대표적으로 이런 것들이 있다. 

[링크](https://www.w3schools.com/js/js_window_navigator.asp)



### Pop-up Alert

자바스크립트에는 세가지 종류의 popup 창이 있다. 

1. Alert box : 단순 확인 창(메세지 + 확인)
2. Confirm box : 취소 / 확인 확인하는 창
3. Prompt box : 사용자가 입력하는 창 (입력란과 취소 / 확인)

[링크](https://www.w3schools.com/js/js_popup.asp)



### Timing*

`window` 객체는 특정한 시간 간격에 따라 코드의 실행이 이루어지게 할 수 있다. 그 특정한 시간 간격을 'timing event'라고 한다. 자바스크립트에서 지원하는 timing event 관련 두가지 함수는 다음과 같다. 

- `setTimeout(*function, milliseconds*`)
  - 특정 millisecond 이후에 특정 함수가 실행된다. 
- `setInterval(*function, milliseconds*`)
  - 위의 함수와 동일하지만 위의 함수는 한번 실행된다면 이 함수는 특정 millisecond간격으로 계속해서 실행된다. 

위의 두 함수를 정지하는 두가지 함수는 다음과 같다. 

- `clearTimeout(*timeoutVariable*)`

  - `setTimeout()`함수에서 리턴된 변수를 인자로 사용한다. `setTimeout()` 함수가 아직 실행하지 않았다면 `clearTimeout()`함수를 통해 종료할 수 있다. 

    > myVar = setTimeout(*function*, *milliseconds*);
    > clearTimeout(myVar); 

- `clearInterval(*timerVariable*)`
  - `setInterval()`함수에서 리턴된 변수를 인자로 사용한다. 

    > myVar = setInterval(*function*, *milliseconds*);
    > clearInterval(myVar);

[링크](https://www.w3schools.com/js/js_timing.asp)



### Cookies**

쿠키는 웹을 공부할 때, 특히 프론트엔드를 공부할 때 매우 중요한 개념이다. 쿠키와 세션은 웹을 공부할 때 기본적으로 알아야 하는 개념인데 쿠키는 클라이언트에서 사용되는 것이고 세션은 백엔드에서 사용되는 것이다. 쿠키는 사용자에 대한 데이터로 사용자의 컴퓨터의 특정 위치에 작은 텍스트파일로 저장된다. 서버가 클라이언트에게 페이지를 주고 나면 사용자에 대한 정보를 잃어버리기 때문에 그것에 대한 대안으로 사용자에 대한 정보를 기억하기 위해 쿠키가 나오게 되었다. 세션은 예를 들면 백엔드에서 로그인을 한번 하고 나서 로그인을 했다는 정보를 가지고 로그인 페이지를 계속 보여주는 개념이다. 쿠키와 세션 모두 편의에 따라 저장하게 되는데 쿠키는 상대적으로 별로 중요하지 않은 것들을 저장하게 된다(아이디, 3일동안 보이지 않기 등 / 암호같은 건 절대로 쿠키로 저장하면 안된다). 

쿠키와 세션 모두 생성-가져오기-삭제가 가능하다. 쿠키를 구현할 때 이미 잘 만들어진 함수들을 가져다 쓰면 되지만 기본적으로 어떤 방식으로 구현하는지 이해는 하고 있어야 한다. 

**쿠키 만드는 법 (이름, 유효시간, 사용되는 경로)**

~~~javascript
document.cookie = "username=John Doe; expires=Thu, 18 Dec 2013 12:00:00 UTC; path=/";
~~~

**쿠키 수정하는 법 (다시 입력하면 됨 )**

~~~javascript
document.cookie = "username=John Smith; expires=Thu, 18 Dec 2013 12:00:00 UTC; path=/";
~~~

**쿠키 삭제하는 법 (이름 삭제하고 날짜 옛날 날짜로 바꿔버리면 됨)**

~~~javascript
document.cookie = "username=; expires=Thu, 01 Jan 1970 12:00:00 UTC; path=/";
~~~

