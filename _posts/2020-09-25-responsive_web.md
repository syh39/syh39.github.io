---
title:  "Responsive Web이란 무엇인가"
excerpt: ""

categories:
  - Web
  - HTML
  - CSS
tags:
  - Web
  - HTML
  - CSS
last_modified_at: 2020-09-25 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

---
## Responsive Web이란 무엇인가

Responsive Web은 데스크탑, 스마트폰, 태블릿같이 다양한 기기에서 사용자가 웹사이트를 사용하기 편하고 보기 좋게 바꿔주는 기술이다. Responsive Web은 특정 프로그램이나 Javascript언어가 아닌 HTML과 CSS만으로 구현될 수 있다. 

>  Responsive Web 예시 - 데스크탑 화면

![R_web](/assets/images/Responsive_web/desktop_example.jpg)



>  Responsive Web 예시 - 스마트폰 화면

![R_web](/assets/images/Responsive_web/phone_example.jpg)

### 

>  Responsive Web 예시 - 태블릿 화면

![R_web](/assets/images/Responsive_web/tablet_example.jpg)

### 

### HTML의 기본 문법



#### 1. HTML의 기본 구조

```html
<!DOCTYPE html>  
<!--모든 HTML 문서는 위쪽과 같이 해당 문서가 HTML 문서라는 선언 문구로 시작한다-->
<!--이 안의 글자들은 모두 주석이다-->
<!--기본적으로 HTML은 태그로 표현이 되는데 태그의 시작과 끝은 각각 <태그이름>, </태그이름>의 형식으로 표현되지만 예외사항도 존재한다-->  

<html>
<body>

<h1>My First Heading</h1>
<h2>My First Heading</h2>
<h3>My First Heading</h3>
<h4>My First Heading</h4>
<h5>My First Heading</h5>
<h6>My First Heading</h6> 
<!--<h1>부터 <h6>는 문서의 헤딩을 표현하는 태그이다. <h1>이 가장 큰 헤딩이고 <h6>로 갈수록 헤딩의 크기가 작아진다-->
  
<p>My first paragraph.</p>
<!--paragraph를 표시하는 태그이다-->

</body> <!--HTML 문서에서 시각적으로 사용자에게 보여지는 부분은 <body>와 </body> 사이에 있는 부분이다-->
</html> <!--모든 HTML 문서는 <html>로 시작해 </html>로 끝난다-->

```

**결과**

![html1](/assets/images/html_css/result1.jpg)




