---
title:  "Javascript 정리 1"
excerpt: ""

categories:
  - Web
tags:
  - Web
  - Javascript
last_modified_at: 2021-01-12 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---



### Javascript란

- Javascript는 웹의 프로그래밍 언어이다 
- Javascript는 객체 기반의 [스크립트 프로그래밍 언어](https://ko.wikipedia.org/wiki/스크립트_언어)이다
- Javascript는 세계에서 가장 인기가 많은 언어이다



### HTML / CSS / Javascript 의 관계

**HTML** 

- 웹의 구조를 담당하며 웹페이지에서 제목, 이미지, 동영상, 문단, 표 등을 정의하는 정적 언어이다.
- 웹의 **구조**를 담당한다.

**CSS** 

- 마크업 언어(HTML, XML, XHML 등)가 실제 표시되는 방법(색상, 레이아웃, 크기, 폰트 등)을 지정하여 콘텐츠 구조를 꾸며주는 정적 언어이다.
- 웹의 **스타일**을 담당한다.

**Javascript** 

- HTML 문서의 정적이고 단조로운 한계를 극복하기 위하여 Netscape사가 만든 Livescript가 이름이 변경된 것으로 브라우저 자체에서 내장된 해석기능을 이용한 클라이언트 기반의 스크립트 언어이다.

- 콘텐츠를 바꾸고 움직이는 등 페이지를 동적으로 꾸며주는 역할을 하는 프로그래밍 언어이다.

- 웹의 **동적 처리**(HTML 요소의 내용 변경, HTML 요소의 속성 변경, CSS 스타일 변경, HTML 요소 숨기기, HTML 요소 보이기 등)를 담당한다.

  

### Javascript 코드의 위치

자바스크립트 코드는 'script'라는 태그 안에 적게 되는데 HTML 문서 안에서 여러 위치에 존재할 수 있다.

- head 안

~~~html
<!DOCTYPE html>
<html>
<head>
<script>
function myFunction() {
  document.getElementById("demo").innerHTML = "Paragraph changed.";
}
</script> 
</head> 
<body>

<h2>JavaScript in Head</h2>
<p id="demo">A Paragraph.</p>
<button type="button" onclick="myFunction()">Try it</button>

</body>
</html>

~~~

- body 안

~~~html
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript in Body</h2>
<p id="demo">A Paragraph.</p>
<button type="button" onclick="myFunction()">Try it</button>

<script>
function myFunction() {
  document.getElementById("demo").innerHTML = "Paragraph changed.";
}
</script>

</body>
</html> 
~~~

- 외부 파일

~~~html
<!DOCTYPE html>
<html>
<body>

<h2>External JavaScript</h2>
<p id="demo">A Paragraph.</p>
<button type="button" onclick="myFunction()">Try it</button>
<p>(myFunction is stored in an external file called "myScript.js")</p>

<script src="myScript.js"></script>

</body>
</html>


~~~

- 외부 URL

~~~html
<!DOCTYPE html>
<html>
<body>

<h2>External JavaScript</h2>
<p id="demo">A Paragraph.</p>
<button type="button" onclick="myFunction()">Try it</button>
<p>(myFunction is stored in an external file called "myScript.js")</p>

<script src="https://www.w3schools.com/js/myScript.js"></script>

</body>
</html>

~~~

- 외부 폴더

~~~html
<!DOCTYPE html>
<html>
<body>

<h2>External JavaScript</h2>
<p id="demo">A Paragraph.</p>
<button type="button" onclick="myFunction()">Try it</button>
<p>(myFunction is stored in an external file called "myScript.js")</p>

<script src="/js/myScript.js"></script>

</body>
</html>


~~~



### Comments

자바스크립트에서 주석은 C언어와 동일한 방식을 사용한다.

~~~javascript
// 한줄 주석

/* 
여러 줄 주석
1 자바스크립트
2 여러줄
3 주석처리
*/
~~~



### Variables

기본적으로 자바스크립트는 모든 변수를 var 타입으로 선언한다. var는 다이나믹 타입이라 한 변수에 number타입의 값을 넣었다가 string타입의 값을 넣을 수 있다.  

~~~javascript
var x = 5.5;   // Number 타입 변수
var y = 6;
var z = x + y;
var k = 123e-5;     // 0.00123
var p = 6;
(y==p)    // Returns true  
(y==x)    // Returns false

typeof p   // returns "number"
p="now string"  // ""로 저장하면 string 타입으로 변수로 저장된다
typeof p   // returns "string"

var person = "John Doe", carName = "Volvo", price = 200; // 콤마를 통해 한꺼번에 여러 변수들을 선언할 수 있다
var person = "John Doe",
carName = "Volvo",
price = 200; // 콤마를 통해 여러줄도 가능

var $myMoney = 5;
var $$$ = "Hello World";  // 자바스크립트에서 달러표시는 평범한 글자로 취급된다 

var txt1 = "John";
var txt2 = "Doe";
var txt3 = txt1 + " " + txt2;  // 텍스트도 간단하게 붙여서 저장할 수 있다
~~~



### Operators

~~~javascript
/* Assignment Operators */
x += y	 // x = x + y
x -= y	 // x = x - y
x *= y	 // x = x * y
x /= y	 // x = x / y
x %= y	 // x = x % y 
x **= y	 // x = x ** y (== x^y)

/* Comparison Operators */
==	 // equal to
===	 // equal value and equal type
!=	 // not equal
!==	 // not equal value or not equal type
>	   // greater than
<	   // less than
>=	 // greater than or equal to
<=	 // less than or equal to
?	   // ternary operator (삼항연산자)
  
/* Logical Operators */
&&	 // logical and
||	 // logical or
!	   // logical not
~~~



### Data Types

~~~javascript
/* Number */
var length = 16;                               

/* String */
var lastName = "Johnson";   

/* Boolean */
var isTrue = true;

/* Array */
var cars = ["Saab", "Volvo", "BMW"];

/* Object */
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};

/* Undefined */
var car;    // Value is undefined, type is undefined

/* Null */
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
person = null;    // Now value is null, but type is still an object
// null은 'nothing'의 의미를 가지고 있다. 자바스크립트에서 null의 타입은 object이다. 
// 위의 방식으로 person이라는 object를 비울 수 있다. 

/* Undefined와 Null의 차이 */
typeof undefined           // undefined 
typeof null                // object
null === undefined         // false (타입이 같지는 않다)
null == undefined          // true (undefined가 null의 값을 가지고 있다)

/* 정리 */
// 1. Primitive Data
// The typeof operator can return one of these primitive types:
// string / number / boolean / undefined
typeof "John"              // Returns "string"
typeof 3.14                // Returns "number"
typeof true                // Returns "boolean"
typeof false               // Returns "boolean"
typeof x                   // Returns "undefined" (if x has no value)

// 2. Complex Data
// The typeof operator can return one of two complex types:
// function / object
typeof {name:'John', age:34} // Returns "object"
typeof [1,2,3,4]             // Returns "object" (not "array")
typeof null                  // Returns "object"
typeof function myFunc(){}   // Returns "function"
~~~



### Functions

자바스크립트에서 함수는 이런 문법을 가진다.

>  function *name*(*parameter1, parameter2, parameter3*) {
>
>  // *code to be executed*
>
>  }

~~~html
<h2>JavaScript Functions</h2>
<p>This example calls a function which performs a calculation and returns the result:</p>

<p id="demo"></p>

<script>
var x = myFunction(4, 3);
document.getElementById("demo").innerHTML = x;

function myFunction(a, b) {
  return a * b;
}
</script>
~~~

- [연습 링크](https://www.w3schools.com/js/tryit.asp?filename=tryjs_function_return)



### Objects

오브젝트는 여러 값들을 넣을 수 있는 변수라고 할 수 있다. 

- Object

~~~javascript
var car = "Fiat"; // simple value

var car = {type:"Fiat", model:"500", color:"white"}; //Object : many values to a variable named car

var person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
}; // Object에서 value들을 담는 변수 이름들을 property(속성)라고 한다. 
~~~

- Object property에 접근하는 두가지 방법

```javascript
person.lastName;    // 방법 1
person["lastName"]; // 방법 2
```

- Object Methods

Object의 속성으로 함수를 포함할 수 있는데 함수 사용시 'this'라는 키워드는 이 함수의 주인, 즉, person object를 의미한다. 따라서 this.firstName이라는 표현은 현재 person object의 firstName 속성을 의미한다.  

```html
<h2>JavaScript Objects</h2>
<p>An object method is a function definition, stored as a property value.</p>

<p id="demo"></p>  
// Shows "John Doe"

<script>
// Create an object:
var person = {
  firstName: "John",
  lastName : "Doe",
  id     : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;  // Returns "John Doe"
  }
};
// Display data from the object:
document.getElementById("demo").innerHTML = person.fullName();  // sets "John Doe to 'demo' id"
</script>
```



### Events

이벤트란 HTML 요소에 '어떤 일'이 일어나는 걸 의미한다. 자바스크립트는 그 '어떤 일'들에 대해 '반응' 할 수 있다. 

> 1. HTML 페이지가 로딩이 완료되었을 때 
> 2. HTML input field가 변했을 떄 
> 3. HTML 버튼이 눌렸을 때 

자바스크립트는 이러한 이벤트들이 감지 되었을 때 특정 반응을 줄 수 있다. 

~~~javascript
<button onclick="this.innerHTML = Date()">The time is?</button>
<button onclick="displayDate()">The time is?</button>
// 버튼이 눌렸을 때 시간을 표시해준다
~~~

- 흔히 쓰이는 이벤트들

  - onchange : HTML 요소의 변화가 생겼을 때 

  - onclick : HTML 요소가 클릭되었을 때 

  - onmouseover :  HTML 요소위로 마우스가 들어왔을 때 

  - onmouseout  :  HTML 요소 밖으로 마우스가 나갔을 때

  - onkeydown : 사용자가 키보드 키를 눌렀을 때 

  - onload : 브라우저가 페이지 로딩을 완료했을 때 

  

### Methods

**String Methods**

~~~javascript
var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
var sln = txt.length; // length라는 속성은 해당 string의 길이를 리턴한다
~~~

- charAt(index) - 문자열에서 인덱스 번호에 해당하는 문자 반환.
- indexOf("찾을 문자") - 문자열에서 왼쪽부터 찾을 문자와 일치하는 문자를 찾아 최초로 일치하는 문자의 인덱스 번호를 반환. 찾는 문자가 없으면 -1 반환.
- lastIndexOf("찾을 문자") - indexOf와 동일하나 문자열의 오른쪽부터 찾음.
- match("찾을 문자") - indexOf와 동일하나 찾는 문자가 없으면 null을 반환.
- replace("바꿀 문자", "새 문자") - 문자열에서 왼쪽부터 바꿀 문자와 일치하는 문자를 찾아 최초로 찾은 문자를 새 문자로 치환.
- search("찾을 문자") - 문자열 왼쪽부터 찾을 문자와 일치하는 문자를 찾아 최초로 일치하는 인덱스 번호를 반환.
- slice(a, b) - a개의 문자를 자르고 b번째 이후에 문자를 자른 후 남은 문자를 반환.
- substring(a, b) - a 인덱스부터 b 인덱스 이전 구간의 문자를 반환.
- substr(a, 문자 개수) - 문자열에 a 인덱스부터 지정한 문자 개수만큼 문자열을 반환.
- split("문자") - 지정한 문자를 기준으로 문자 데이터를 나누어 배열에 저장하여 반환.
- toLowerCase() - 문자열에서 영문 대문자를 모두 소문자로 바꿈.
- toUpperCase() - 문자열에서 영문 소문자를 모두 대문자로 바꿈.
- length - 문자열에서 문자의 개수를 반환.
- concat("새로운 문자") - 문자열에 새로운 문자열을 결합.
- charCodeAt("찾을 문자") - 찾을 문자의 아스키 코드 값을 반환.
- fromCharCode(아스키 코드 값) - 아스키 코드 값에 해당하는 문자를 반환.
- trim() - 문자의 앞 또는 뒤에 공백 문자열을 삭제.



**Array Methods**

~~~javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.join(" * ");   // Banana * Orange * Apple * Mango
~~~

- join(연결문자) - 배열 객체에 데이터를 연결 문자 기준으로 1개의 문자형 데이터로 반환.
- reverse() - 배열 객체에 데이터의 순서를 거꾸로 바꾼 후 반환.
- sort() - 배열 객체에 데이터를 오름차순으로 정렬.
- slice(index1, index2) - 배열 객체에 데이터 중 원하는 인덱스 구간만큼 잘라서 배열 객체로 가져옴.
- splice() - 배열 객체에 지정 데이터를 삭제하고 그 구간에 새 데이터를 삽입할 수 있음.
- concat() - 2개의 배열 객체를 하나로 결합.
- pop() - 배열에 저장된 데이터 중 마지막 인덱스에 저장된 데이터 삭제.
- push(new data) - 배열 객체에 마지막 인덱스에 새 데이터를 삽입.
- shift() - 배열 객체에 저장된 데이터 중 첫 번째 인덱스에 저장된 데이터를 삭제.
- unshift(new data) - 배열 객체의 가장 앞의 인덱스에 새 데이터를 삽입.
- length - 배열에 저장된 총 데이터의 개수를 반환.



**Math Methods**

- Math.abs(숫자) - 숫자의 절댓값을 반환.
- Math.max(숫자1, 숫자2, 숫자3) - 숫자 중 최댓값을 반환.
- Math.min(숫자1, 숫자2, 숫자3) - 숫자 중 최솟값을 반환.
- Math.pow(숫자, 제곱값) - 숫자의 거듭제곱한 값을 반환.
- Math.random() - 0~1 사이의 난수를 반환.
- Math.round(숫자) - 소수점 첫째 자리에서 반올림하여 정수를 반환.
- Math.ceil(숫자) - 소수점 첫째 자리에서 무조건 올림에서 정수를 반환.
- Math.floor(숫자) - 소수점 첫째 자리에서 무조건 내림해서 정수를 반환.
- Math.sqrt(숫자) - 숫자의 제곱근 값을 반환.
- Math.PI - 원주율 상수를 반환.



**Window Object Methods**

윈도우 객체는 브라우저 객체 모델(BOM - 브라우저에 내장된 객체)의 최상위 객체이다

- open("url 경로", "창 이름", "옵션 설정") - 새 창을 열 때 사용.(open() 메서드 옵션 설정:
- width/height/left/top/location/status/scrollbars/tollbars)
- alert("메세지") - 경고 창을 띄움.
- prompt("질의 내용", "기본 답변") - 질의응답 창을 띄움.
- confirm("질의 내용") - 확인/취소 창을 띄움.(확인 클릭시 true 반환, 취소 클릭시 false 반환.)
- moveTo(x 위치값, y 위치값) - 창의 위치를 이동시킬 때 사용.
- resizeTo(너빗값, 높잇값) - 창의 크기를 변경시킬 때 사용.
- setInterval("스크립트 실행문", 시간 간격) - 일정 간격으로 반복하여 실행문을 실행시킬 때 사용.
- clearIntervar(참조 변수) - 참조 변수에 참조되어 있는 setInterval() 삭제.
- setTimeout("스크립트 실행문", 시간 간격) - 일정 간격으로 한 번만 실행문을 실행시킬 때 사용.
- clearTimeout(참조 변수) - 참조 변수에 참조되어 있던 setTimeout() 삭제.

[Method 더보기](https://www.theteams.kr/teams/2440/post/67294)



### Conditions

기본적으로 자바스크립트에서 조건문은 C언어와 문법이 동일하다.

**If - else**

> if (*condition1*) {
>  // *block of code to be executed if condition1 is true
> *} else if (*condition2*) {
>  // *block of code to be executed if the condition1 is false and condition2 is true*
> } else {
>  // *block of code to be executed if the condition1 is false and condition2 is false
> *}

~~~javascript
if (time < 10) {
  greeting = "Good morning";
} else if (time < 20) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
~~~

**Switch**

> switch(*expression*) {
>  case *x*:
>   *// code block
> \*  break;
>  case *y*:
>   *// code block
> \*  break;
>  default:
>    // *code block*
> }

~~~javascript
switch (new Date().getDay()) {
  case 6:
    text = "Today is Saturday";
    break;
  case 0:
    text = "Today is Sunday";
    break;
  default:
    text = "Looking forward to the Weekend";
}
~~~



### Loops

자바스크립트에선 여러 종류의 반복문을 지원한다. 

- `for` - loops through a block of code a number of times
- `for/in` - loops through the properties of an object
- `for/of` - loops through the values of an iterable object
- `while` - loops through a block of code while a specified condition is true
- `do/while` - also loops through a block of code while a specified condition is true

**For**

> for (*statement 1*; *statement 2*; *statement 3*) {
>
> // *code block to be executed*
>
> }

~~~html
<p id="demo"></p>

<script>
var cars = ["BMW", "Volvo", "Saab", "Ford", "Fiat", "Audi"];
var text = "";
var i;
for (i = 0; i < cars.length; i++) {
  text += cars[i] + "<br>";
}
document.getElementById("demo").innerHTML = text;
</script>
~~~

**For/in**

Object에서 속성들을 차례로 참조할 때 사용한다

~~~html
<p id="demo"></p>

<script>
var txt = "";
var person = {fname:"John", lname:"Doe", age:25}; 
var x;
for (x in person) {
  txt += person[x] + " ";
}
document.getElementById("demo").innerHTML = txt;
</script>
~~~

**For/of**

Array, String, Map, NodeList 등에서 사용 가능하다

~~~html
<p>The for/of statement loops through the values of an iterable object.</p>

<script>
var cars = ["BMW", "Volvo", "Mini"];
var x;

for (x of cars) {
  document.write(x + "<br >");
}
</script>
~~~

**While**

>while (*condition*) {
>
>*// code block to be executed*
>
>}

~~~html
<p id="demo"></p>

<script>
var text = "";
var i = 0;
while (i < 10) {
  text += "<br>The number is " + i;
  i++;
}
document.getElementById("demo").innerHTML = text;
</script>
~~~

**Do/While**

>do {
>
>// code block to be executed
>
>*}*
>
>
>while (condition);

~~~html
<p id="demo"></p>

<script>
var text = ""
var i = 0;

do {
  text += "<br>The number is " + i;
  i++;
}
while (i < 10);
document.getElementById("demo").innerHTML = text;
</script>
~~~





- [W3Schools Source](https://www.w3schools.com/js/js_examples.asp)

- [참고 출저](https://www.theteams.kr/teams/2440/post/67294)
