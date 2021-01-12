---
title:  "Javascript HTML DOM"
excerpt: "HTML DOM(Document Object Model)은 웹페이지를 구성하고 있는 모든 요소들을 일종의 객체로 만들어서 자바스크립트가 제어할 수 있도록 한 것이다."

categories:
  - Web
tags:
  - Web
  - Javascript
last_modified_at: 2021-01-13 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

### HTML DOM

HTML DOM(Document Object Model)은 웹페이지를 구성하고 있는 모든 요소들을 일종의 객체로 만들어서 자바스크립트가 제어할 수 있도록 한 것이다.  웹 페이지가 전부 로드 되면 브라우저는 페이지의 DOM을 구성한다. HTML DOM 모델은 객체들의 트리 구조로 만들어진다. 

![DOM](https://www.w3schools.com/js/pic_htmltree.gif)

HTML DOM은 자바스크립트(혹은 다른 언어)가 프로그래밍적으로 접근하고 변환하기위한 프로그래밍 인터페이스라고 할 수 있다. 자바스크립트는 웹브라우저 위에서 실행되긴 하지만 엄밀히 말하면 자바스크립트는 언어이고 웹브라우저는 언어가 제어하는 대상이라고 생각할 수 있다. 자바스크립트는 웹브라우저에서만 실행되는게 아니라 플래시 플레이어에서도 액션스크립트의 형태로 쓰인다. Node.js라는 언어 역시도 자바스크립트의 문법을 채용하고 있는데 자바스크립트와 달리 서버쪽의 자원을 핸들링할 때 쓰인다. 즉, 돔은 자바스크립트가 웹페이지를 핸들링하기 위한 프로그래밍 인터페이스다. 자바스크립트는 돔을 제어하는 방식으로 웹페이지를 제어한다.

도큐먼트 오브젝트 모델을 통해서 자바스크립트가 할 수 있는 일들은 다음과 같다.

- 자바스크립트는 페이지 내의 모든 HTML 요소들을 바꿀 수 있다.
- 자바스크립트는 페이지 내의 모든 HTML 속성들을 바꿀 수 있다. 
- 자바스크립트는 페이지 내의 모든 CSS 스타일들을 바꿀 수 있다. 
- 자바스크립트는 페이지 내의 모든 존재하는 HTML 요소들과 속성들을 지울 수 있다. 
- 자바스크립트는 새로운 HTML 요소들과 속성들을 만들 수 있다. 
- 자바스크립트는 페이지 내에서 일어나는 모든 HTML 이벤트들에 대해 반응할 수 있다. 
- 자바스크립트는 페이지 내에서 새로운 HTML 이벤트를 만들 수 있다.  

요약하자면, HTML DOM은 어떻게 HTML 요소들을 참조하고, 바꾸고, 추가하고, 삭제하는지에 대한 기준이다. 



### Method & Property

- HTML DOM Method : HTML 요소에 자바스크립트가 하는 액션
- HTML DOM Property : 자바스크립트를 통해 설정하거나 바꿀 수 있는 HTML 요소의 값

~~~html
<!DOCTYPE html>
<html>
<body>

<h2>My First Page</h2>

<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = "Hello World!";
</script>

</body>
</html>
~~~

이 경우 `getElementById`는 **method**이고, `innerHTML` is a **property**이다.



### DOM Document

HTML DOM Document는 웹 페이지 내의 모든 오브젝트들을 소유하고 있는 오브젝트이다. 웹 페이지 내의 어떤 HTML 요소에 접근하든 항상 document 오브젝트에 먼저 접근해야 한다. Document 오브젝트를 이용해 HTML을 조작하는 대표적인 예시들은 아래와 같다. 



**Finding HTML Elements**

| Method                                  | Description                   |
| :-------------------------------------- | :---------------------------- |
| document.getElementById(*id*)           | Find an element by element id |
| document.getElementsByTagName(*name*)   | Find elements by tag name     |
| document.getElementsByClassName(*name*) | Find elements by class name   |



**Changing HTML Elements**

| Property                                 | Description                                   |
| :--------------------------------------- | :-------------------------------------------- |
| *element*.innerHTML = *new html content* | Change the inner HTML of an element           |
| *element*.*attribute = new value*        | Change the attribute value of an HTML element |
| *element*.style.*property = new style*   | Change the style of an HTML element           |

| Method                                     | Description                                   |
| :----------------------------------------- | :-------------------------------------------- |
| *element*.setAttribute*(attribute, value)* | Change the attribute value of an HTML element |



**Adding and Deleting Elements**

| Method                            | Description                       |
| :-------------------------------- | :-------------------------------- |
| document.createElement(*element*) | Create an HTML element            |
| document.removeChild(*element*)   | Remove an HTML element            |
| document.appendChild(*element*)   | Add an HTML element               |
| document.replaceChild(*new, old*) | Replace an HTML element           |
| document.write(*text*)            | Write into the HTML output stream |



**Adding Events Handlers**

| Method                                                     | Description                                   |
| :--------------------------------------------------------- | :-------------------------------------------- |
| document.getElementById(*id*).onclick = function(){*code*} | Adding event handler code to an onclick event |



**Finding HTML Objects**

The first HTML DOM Level 1 (1998), defined 11 HTML objects, object collections, and properties. These are still valid in HTML5.

Later, in HTML DOM Level 3, more objects, collections, and properties were added.

| Property                     | Description                                                  | DOM  |
| :--------------------------- | :----------------------------------------------------------- | :--- |
| document.anchors             | Returns all <a> elements that have a name attribute          | 1    |
| document.applets             | Returns all <applet> elements (Deprecated in HTML5)          | 1    |
| document.baseURI             | Returns the absolute base URI of the document                | 3    |
| document.body                | Returns the <body> element                                   | 1    |
| document.cookie              | Returns the document's cookie                                | 1    |
| document.doctype             | Returns the document's doctype                               | 3    |
| document.documentElement     | Returns the <html> element                                   | 3    |
| document.documentMode        | Returns the mode used by the browser                         | 3    |
| document.documentURI         | Returns the URI of the document                              | 3    |
| document.domain              | Returns the domain name of the document server               | 1    |
| document.domConfig           | Obsolete. Returns the DOM configuration                      | 3    |
| document.embeds              | Returns all <embed> elements                                 | 3    |
| document.forms               | Returns all <form> elements                                  | 1    |
| document.head                | Returns the <head> element                                   | 3    |
| document.images              | Returns all <img> elements                                   | 1    |
| document.implementation      | Returns the DOM implementation                               | 3    |
| document.inputEncoding       | Returns the document's encoding (character set)              | 3    |
| document.lastModified        | Returns the date and time the document was updated           | 3    |
| document.links               | Returns all <area> and <a> elements that have a href attribute | 1    |
| document.readyState          | Returns the (loading) status of the document                 | 3    |
| document.referrer            | Returns the URI of the referrer (the linking document)       | 1    |
| document.scripts             | Returns all <script> elements                                | 3    |
| document.strictErrorChecking | Returns if error checking is enforced                        | 3    |
| document.title               | Returns the <title> element                                  | 1    |
| document.URL                 | Returns the complete URL of the document                     | 1    |

