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

*선택자 우선순위 : id 선택자 > class 선택자 > tag 선택자*
