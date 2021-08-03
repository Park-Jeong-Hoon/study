># CSS 공부 정리
css 구성요소 : 선택자, 속성<br>
css 적용방법 2가지<br>
1. style 태그 이용하기<br>
```html
<head>
    <title>css study</title>
    <meta charset="UTF-8">
    <style>
        a {
            color:black;
            text-decoration: none;
        }
    </style>
</head>
<body>
<a href="html">HTML</a>
</body>
</html>
```
<br>

2. 원하는 태그 안에다 style 속성 이용하기
```html
<head>
    <title>css study</title>
    <meta charset="UTF-8">
</head>
<body>
<a href="html" style="color:black;text-decoration:none">HTML</a>
</body>
</html>
```

*선택자 우선순위 : id 선택자 > class 선택자 > tag 선택자*<br>

CSS 박스모델<br>
아래 코드를 실행 시 h1태그로 감싸준 단어는 단어가 속해있는 라인 전체가, a태그로 감싸준 단어는 단어부분만 박스가 감싼다. 이는 h1태그는 block level element, a태그는 inline element 이기 때문이다. 
```html
<!DOCTYPE HTML>
<html>
<head>
    <meta charset="UTF-8">
    <title></title>
    <style>
        /*
        block level element
         */
        h1 {
            /*border-width: 5px;
            border-color: red;
            border-style: solid;*/
            border:5px solid red; /*위의 코드를 이렇게 줄일 수 있음*/
        }
        /*
        inline element
         */
        a {
            border-width: 5px;
            border-color: red;
            border-style: solid;
        }
    </style>
</head>
<body>
<h1>CSS</h1>
<a>CSS</a>
</body>
</html>
```

하지만 display속성을 이용함으로써 이런 성질들을 변경시킬 수가 있다. 아래 코드 처럼 display속성을 이용해주면 위와 반대의 결과가 나오는 것을 확인할 수 있다.
```html
<!DOCTYPE HTML>
<html>
<head>
    <meta charset="UTF-8">
    <title></title>
    <style>
        /*
        block level element
         */
        h1 {
            border-width: 5px;
            border-color: red;
            border-style: solid;
            display: inline;
        }
        /*
        inline element
         */
        a {
            border-width: 5px;
            border-color: red;
            border-style: solid;
            display: block;
        }
    </style>
</head>
<body>
<h1>CSS</h1>
<a>CSS</a>
</body>
</html>
```
또한 태그로 둘러쌓인 부분을 안보이게 하고 싶을 경우에는 disply:none;으로 해주면 된다.<br><br>

padding을 이용해 박스와 박스 속 단어 사이의 간격을 조절할 수 있고 margin을 이용해 박스와 박스 외부 사이의 간격을 조절할 수가 있다. width, height를 이용하면 가로 세로 폭을 지정할 수 있다.
```css
        h1 {
            border:5px solid red;
            padding: 20px;
            margin: 20px;
            width: 100px;
            height: 100px;
        }
```

그리드<br>
Korea, 대한민국 두 단어를 수평으로 나열하면서 표처럼 나눠주고 싶을 때 아래 코드와 같이 하면 된다.
```html
<!DOCTYPE HTML>
<html>
<head>
    <title></title>
    <meta charset="UTF-8">
    <style>
        #grid {
            border: 5px solid lightpink;
            display: grid;
            grid-template-columns: 100px 1fr; /*앞에 100px는 첫번쨰 컬림 길이, 뒤에 1fr은 남는 공간 길이*/
            /*grid-template-columns: 1fr 1fr; 이런식으로 해주면 비율, 1:1 (첫번째 컬럼:두번째 컬럼)*/
        }
        div {
            border: 5px solid skyblue;
        }
    </style>
</head>
<body>
<div id="grid"> <!--Korea, 대한민국을 나란히 놓기 위한 부모 태그-->
    <div>Korea</div> <!--의미 없는 태그, 오로지 디자인을 위함 -->
    <div>대한민국</div>
</div>
</body>
</html>
```

<br>미디어쿼리 -> @media를 이용해서 반응형 웹사이트를 만들 수가 있다.<br>
아래 코드를 실행 시켜주면 웹페이지의 가로 크기에 변화를 주다보면 500px 이하일 때는 '반응형 웹사이트'라는 문구와 이를 둘러싼 테두리가 보이지 않게 된다.
```html
<!DOCTYPE HTML>
<html>
<head>
    <title></title>
    <meta charset="UTF-8">
    <style>
        div {
            border: 10px solid black;
            font-size: 50px;
        }
        @media (max-width: 500px) {
            div {
                display: none;
            }
        }
    </style>
</head>
<body>
<div>
    반응형 웹사이트
</div>
</body>
</html>
```

<br>style태그 안에 있는 CSS코드를 css파일을 별도로 만들어 거기에 저장해서 같은 CSS를 여러 파일에 적용할 수가 있다. css파일을 다른 파일에서 이용하려면 head태그 안에 아래의 코드를 작성하면 된다. (css파일명이 style 일 경우를 예시로 듬)
```html
<link rel="stylesheet" href="style.css">
```
