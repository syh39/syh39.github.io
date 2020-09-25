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

>  Responsive Web 예시 - 레이아웃

![R_web](/assets/images/Responsive_web/responsive_web_example.jpg)

 

>  Responsive Web 예시 - 데스크탑 화면

![R_web](/assets/images/Responsive_web/desktop_example.jpg)



>  Responsive Web 예시 - 스마트폰 화면

![R_web](/assets/images/Responsive_web/phone_example.jpg)



>  Responsive Web 예시 - 태블릿 화면

![R_web](/assets/images/Responsive_web/tablet_example.jpg)



위의 사진들을 보면 각 기기마다 웹사이트의 레이아웃이 바뀐 것을 확인할 수 있다. 이렇게 기기별로 각각의 화면을 구성해주는 기술이 Responsive Web이다. 



## Responsive Web Design 관련 tag 및 css



### 1. meta viewport

Viewport 사용자의 디바이스 화면에서 보여지는 영역을 의미한다. 원래 웹 페이지는 데스크탑에서만 동작했지만 스마트폰과 태블릿의 출현으로 작은 화면으로 웹 페이지를 사용하는 데에 불편함이 있었기 때문에 스마트폰과 태블릿에서도 편리하게 웹 페이지를 사용할 수 있도록 하는 responsive web이 등장했다. 그런 관점에서 viewport는 특정 기기에서 웹 페이지를 볼 수 있는 크기, 즉 해당 디바이스의 화면의 크기를 의미한다. 

~~~html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    img{
      max-width: 100%;
      height: auto;
    }
  </style>
</head>
~~~

Viewport는 meta 태그 안에서 사용이 되는데 보통 meta 태그는 검색 엔진에게 해당 사이트가 어떤 용도의 사이트인지 알려주는 용도로도 사용이 된다. 여기서 meta 태그는 viewport를 만드는 데에 사용이 된다.  위의 코드의 경우 'content' 속성의 'width=device-width' 라는 것은 넓이를 화면의 넓이로 맞춘다는 뜻이고 'initial-scale=1.0'은 브라우저가 처음에 페이지를 로딩했을 때 페이지의 비율이 100%라는 뜻이다. 즉, 위의 코드는 어떤 기기든 100% 크기로 화면에 딱 맞게 보여주라는 코드이다.

>  Meta tag 적용 전과 적용 후

![R_web](/assets/images/Responsive_web/meta_tag.jpg) 



### 2. Grid-View

Grid-view는 웹페이지를 디자인할 때 페이지의 각 요소들을 배치하기 위해 활용하는 세로로 된 가상의 구분선이다. 많은 웹페이지들은 이런 grid-view를 기반으로 만들어져있다. 보통 grid-view는 12개의 column으로 구성되어 있는데 이러한 구성이 웹페이지를 디자인할 때 큰 도움이 된다. 

>  Grid-view 예시 1

![R_web](/assets/images/Responsive_web/gridview_example1.jpg) 



>  Grid-view 예시 2

![R_web](/assets/images/Responsive_web/gridview_example2.jpg) 

Grid-view를 사용하기 위해서는 CSS에 'box-sizing: border-box;' 라는 속성을 추가해줘야 하는데 이 속성은 해당 영역 내에 margin이나 padding을 적용하더라도 해당 영역을 벗어나지 않게 해주는 속성이다. 

~~~html
<!DOCTYPE html>
<html>
<head>
<style> 
.div1 {
  width: 300px;
  height: 100px;
  border: 1px solid blue;
}

.div2 {
  width: 300px;
  height: 100px;  
  padding: 50px;
  border: 1px solid red;
}
</style>
</head>
<body>

<div class="div1">This div is smaller (width is 300px and height is 100px).</div>
<br>
<div class="div2">This div is bigger (width is also 300px and height is 100px).</div>

</body>
</html>

~~~

**결과**

![R_web](/assets/images/Responsive_web/box-sizing_example1.jpg) 

Box-sizing 속성이 적용이 안됐을 때 발생하는 문제점이다. 똑같이 div 태그로 감쌌지만 div2 클래스의 경우 패딩을 주자 크기가 지정되어 있는 width인 300px을 넘어가 버렸다. 아래는 'box-sizing: border-box' 속성을 적용한 코드이다. 

~~~html
<!DOCTYPE html>
<html>
<head>
<style> 
.div1 {
  width: 300px;
  height: 100px;
  border: 1px solid blue;
  box-sizing: border-box;
}

.div2 {
  width: 300px;
  height: 100px;  
  padding: 50px;
  border: 1px solid red;
  box-sizing: border-box;
}
</style>
</head>
<body>

<div class="div1">Both divs are the same size now!</div>
<br>
<div class="div2">Hooray!</div>

</body>
</html>

~~~

**결과**

![R_web](/assets/images/Responsive_web/box-sizing_example2.jpg) 

'box-sizing: border-box' 속성을 한줄만 적용했는데 패딩이 주어져도 지정돼있는 width인 300px을 넘어가지 않았다. 이웹페이지의 요소들을 배치하기 위해 box-sizing 속성이 필요한 이유이다. 

