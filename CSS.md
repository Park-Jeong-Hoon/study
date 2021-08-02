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
또한 태그로 둘러쌓인 부분을 안보이게 하고 싶을 경우에는 disply:none;으로 해주면 된다.<br>

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
