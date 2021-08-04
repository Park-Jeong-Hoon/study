># JavaScript 공부 정리
html파일에 JavaScript파일 추가하기<br>
```html
<body>
    Hello world!!
    <script src="index.js"></script> <!--자바스크립트 파일명.js-->
</body>
```


<br>변수 초기화
```javascript
let a = 1;
console.log(a); //결과 = 1, console.log()를 이용해 콘솔창에 출력 가능
a = 777;
console.log(a); //결과 = 777, let을 이용해 변수를 초기화하면 값을 변경 가능하며 var도 마찬가지이다.
```

```javascript
const a = 1; //const를 이용하면 a는 값을 바꿀 수 없는 상수가 되어서 a의 값을 바꾸려하면 오류가 남.
console.log(a); //결과 = 1
```

```javascript
//다양한 타입 저장 가능
const a = 29; //Int
const b = 14.62; //Float
const c = "great"; //String
const d = true; //Boolean
```
