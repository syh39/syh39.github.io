---
title:  "Javascript 정리 2"
excerpt: ""

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



### Type Conversion

자바스크립트에서 변수들은 다른 종류의 변수로 변환(함수사용 or 자동)될 수 있다.

~~~javascript
/* Number -> String */
String(x)         // returns a string from a number variable x
String(123)       // returns a string from a number literal 123
String(100 + 23)  // returns a string from a number from an expression

x.toString()
(123).toString()
(100 + 23).toString()  // The Number method toString() does the same.

/* Boolean -> String */
String(false)      // returns "false"
String(true)       // returns "true"

false.toString()   
true.toString()    //The Boolean method toString() does the same.

/* Dates -> String */
String(Date())  // returns "Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)"
Date().toString()  // The Date method toString() does the same.

/* String  -> Number */
Number("3.14")    // returns 3.14
Number(" ")       // returns 0
Number("")        // returns 0
Number("99 88")   // returns NaN

/* Unary + Operator */
var y = "5";      // y is a string
var x = + y;      // x is a number

/* Boolean -> Number */
Number(false)     // returns 0
Number(true)      // returns 1

/* Dates -> Number */
d = new Date();
Number(d)          // returns 1404568027739

/* Unary + Operator */
var y = "5";      // y is a string
var x = + y;      // x is a number
~~~



### Error Handling

자바스크립트에서 에러가 발생하면 자바스크립트는 코드를 멈추고 에러메세지를 던진다. 보통 그 과정을 "throw an exception"이라고 표현한다. 

자바스크립트는 내부적으로 Error object를 만드는데 그 안에는 name 속성과 message 속성이 들어있다. 

try 블락 안에는 시도하고자 하는 코드가 들어가는데 이때 에러가 발생 시 에러를 'throw' 할 수 있다.  그렇게 던져진 에러는 catch 블락에서 받아서 처리하게 된다. finally 블락은 에러가 발생하든 안하든 실행되는 블락이다. 

자바스크립트에선 미리 정의되어있는 에러들이 존재한다. (EvalError, RangeError, ReferenceError, SyntaxError, TypeError, URIError)

>try {
>
> Block of code to try
>
>}
>catch(*err*) {
>
> Block of code to handle errors
>
>}
>
>finally {
>
> Block of code to be executed regardless of the try / catch result
>
>}

~~~html
<!DOCTYPE html>
<html>
<body>

<p>Please input a number between 5 and 10:</p>

<input id="demo" type="text">
<button type="button" onclick="myFunction()">Test Input</button>

<p id="p01"></p>

<script>
function myFunction() {
  var message, x;
  message = document.getElementById("p01");
  message.innerHTML = "";
  x = document.getElementById("demo").value;
  try { 
    if(x == "")  throw "is empty";
    if(isNaN(x)) throw "is not a number";
    x = Number(x);
    if(x > 10)   throw "is too high";
    if(x < 5)  throw "is too low";     // throw statement allows you to create a custom error.


  }
  catch(err) {
    message.innerHTML = "Input " + err;  
  } 
  /* If you use throw together with try and catch, 
     you can control program flow and generate custom error messages.*/
  finally {
    document.getElementById("demo").value = "";
  }
}
</script>

</body>
</html>
~~~

- [연습 링크](https://www.w3schools.com/js/tryit.asp?filename=tryjs_finally_error)



### Scope

Scope는 변수들의 접근권한을 결정한다. 함수의 scope 안에서 정의된 변수들은 함수 밖에서 참조할 수 없다. 함수의 scope 바깥에서 선언된 변수는 글로벌 변수가 되는데 스크립트 내의 모든 영역에서 해당 변수를 참조할 수 있다. 



### Let

2015년에 let과 const라는 두가지 키워드가 추가되었는데 이 두가지 키워드는 Block Scope 변수를 제공한다. 

~~~javascript
{
  var x = 2;
}
// x CAN be used here / 기존의 var 키워드는 block scope의 개념이 없다(함수 scope만 가지고 있다)

{
  let x = 2;
}
// x can NOT be used here / let 키워드는 block scope를 가진다. 
~~~

**변수 재선언의 경우**

~~~javascript
var x = 10;
// Here x is 10
{
  var x = 2;
  // Here x is 2
}
// Here x is 2  // 기존의 var 키워드의 경우 block scope의 개념이 없기 때문에 block안에서 재선언한 경우 block 밖의 변수에도 영향을 미치는 문제가 있었다.

var x = 10;
// Here x is 10
{
  let x = 2;
  // Here x is 2
}
// Here x is 10 // 위의 문제를 해결하기 위해 block 내에서 let 키워드를 사용하면 block 밖의 변수에 영향을 미치지 않을 수 있다. 
~~~

**loop에서 활용**

~~~javascript
var i = 5;
for (var i = 0; i < 10; i++) {
  // some statements
}
// Here i is 10

let i = 5;
for (let i = 0; i < 10; i++) {
  // some statements
}
// Here i is 5
~~~

**function 안과 function 밖에서의 경우**

~~~javascript
function myFunction() {
  var carName = "Volvo";   // Function Scope
}

function myFunction() {
  let carName = "Volvo";   // Function Scope
}
// 함수 내에선 동일한 Scope를 가진다. 

var x = 2;       // Global scope
let x = 2;       // Global scope
// 함수 밖에선 동일한 Scope를 가진다. 
~~~

**재선언의 경우**

~~~javascript
var x = 2;       // Allowed
let x = 3;       // Not allowed

{
  var x = 4;   // Allowed
  let x = 5   // Not allowed
}
// var 키워드로 변수를 재선언하는건 어디에서든지 가능하다. 
// 하지만 같은 scope(혹은 block)내에서 var로 선언된 변수를 let로 재선언하는건 불가능하다. 
/* ------------------------------------------------------------- */

let x = 2;       // Allowed
let x = 3;       // Not allowed
{
  let x = 4;   // Allowed
  let x = 5;   // Not allowed
} 
// 같은 scope(혹은 block)내에서 let로 선언된 변수를 let로 재선언하는건 불가능하다. 
/* ------------------------------------------------------------- */

let x = 2;       // Allowed
var x = 3;       // Not allowed
{
  let x = 4;   // Allowed
  var x = 5;   // Not allowed
} 
// 같은 scope(혹은 block)내에서 let로 선언된 변수를 var로 재선언하는건 불가능하다. 
/* ------------------------------------------------------------- */


let x = 2;       // Allowed

{
  let x = 3;   // Allowed
}

{
  let x = 4;   // Allowed
}
// 다른 scope(혹은 block)에서 let변수를 let로 재선언하는 것은 가능하다
/* ------------------------------------------------------------- */
~~~



### Const

Const는 let과 동일한 성질을 가지는데 let과 다른점은 재선언이 안된다. 

~~~javascript
const PI;
PI = 3.14159265359; // (X)

const PI = 3.14159265359; // (O) 
// const는 선언과 동시에 값이 할당되어야 한다
/* ------------------------------------------------------------- */

const PI = 3.141592653589793;
PI = 3.14;      // This will give an error
PI = PI + 10;   // This will also give an error
// primitive value의 경우 한번 주어진 값은 다시 바꿀 수 없다
/* ------------------------------------------------------------- */


const car = {type:"Fiat", model:"500", color:"white"}; // You can create a const object:

car.color = "red"; // You can change a property:
car.owner = "Johnson"; // You can add a property:
// primitive value와 다르게 Constant Object(혹은 Array)의 경우 속성은 변경할 수 있다. 재할당이 안될 뿐이다. 
// ex)
const car = {type:"Fiat", model:"500", color:"white"};
car = {type:"Volvo", model:"EX60", color:"red"};    // ERROR
/* ------------------------------------------------------------- */

var x = 10;
// Here x is 10
{
  const x = 2;
  // Here x is 2
}
// Here x is 10
// let과 동일
/* ------------------------------------------------------------- */

var x = 2;         // Allowed
const x = 2;       // Not allowed
{
  let x = 2;     // Allowed
  const x = 2;   // Not allowed
}
// 같은 scope(혹은 block)내에서 var이나 let으로 선언된 변수를 const로 재선언하는건 불가능하다
/* ------------------------------------------------------------- */

const x = 2;       // Allowed
const x = 3;       // Not allowed
x = 3;             // Not allowed
var x = 3;         // Not allowed
let x = 3;         // Not allowed

{
  const x = 2;   // Allowed
  const x = 3;   // Not allowed
  x = 3;         // Not allowed
  var x = 3;     // Not allowed
  let x = 3;     // Not allowed
}
// 같은 scope(혹은 block)내에서 const로 선언된 변수를 const로 재선언하는건 불가능하다
/* ------------------------------------------------------------- */

const x = 2;       // Allowed

{
  const x = 3;   // Allowed
}

{
  const x = 4;   // Allowed
}
// 다른 scope(혹은 block)에서 const변수를 const로 재선언하는 것은 가능하다
/* ------------------------------------------------------------- */
~~~



### Classes



### Forms





- [W3Schools Source](https://www.w3schools.com/js/js_examples.asp)
