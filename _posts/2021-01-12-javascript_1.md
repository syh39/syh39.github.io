---
title:  "Javascript 정리 1"
excerpt: ""

categories:
  - Web
tags:
  - Web
  - HTML
last_modified_at: 2020-09-13 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---



### Javascript란

- Javascript는 객체 기반의 [스크립트 프로그래밍 언어](https://ko.wikipedia.org/wiki/스크립트_언어)이다
- Javascript는 웹의 프로그래밍 언어이다 
- Javascript는 세계에서 가장 인기가 많은 언어이다



### HTML / CSS / Javascript 의 관계

#### HTML 

- 웹의 구조를 담당하며 웹페이지에서 제목, 이미지, 동영상, 문단, 표 등을 정의하는 정적 언어이다.
- 웹의 **구조**를 담당한다.

#### CSS 

- 마크업 언어(HTML, XML, XHML 등)가 실제 표시되는 방법(색상, 레이아웃, 크기, 폰트 등)을 지정하여 콘텐츠 구조를 꾸며주는 정적 언어이다.
- 웹의 **스타일**을 담당한다.

#### Javascript 

- HTML 문서의 정적이고 단조로운 한계를 극복하기 위하여 Netscape사가 만든 Livescript가 이름이 변경된 것으로 브라우저 자체에서 내장된 해석기능을 이용한 클라이언트 기반의 스크립트 언어이다.

- 콘텐츠를 바꾸고 움직이는 등 페이지를 동적으로 꾸며주는 역할을 하는 프로그래밍 언어이다.

- 웹의 **동적 처리**(HTML 요소의 내용 변경, HTML 요소의 속성 변경, CSS 스타일 변경, HTML 요소 숨기기, HTML 요소 보이기 등)를 담당한다.

  

### Javascript 코드의 위치

자바스크립트 코드는 'script'라는 태그 안에 적게 되는데 HTML 문서 안에서 여러 위치에 존재할 수 있다.

#### head 안

~~~Javascript
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

#### body 안

~~~javascript
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

#### 외부 파일

~~~javascript
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

#### 외부 URL

~~~javascript
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

#### 외부 폴더

~~~javascript
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
>  // *code to be executed*
> }

~~~javascript
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

~~~javascript
var car = "Fiat"; // simple value

var car = {type:"Fiat", model:"500", color:"white"}; //Object : many values to a variable named car

var person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
}; // Object에서 value들을 담는 변수 이름들을 property(속성)라고 한다. 

/* Object property에 접근하는 두가지 방법 */
person.lastName;    // 방법 1
person["lastName"]; // 방법 2
~~~



#### Object property에 접근하는 두가지 방법

>person.lastName;   
>person["lastName"]; 

### Events



### Objects



### Methods



### Conditions





### Loops









[정리 Source](https://www.w3schools.com/js/js_examples.asp)