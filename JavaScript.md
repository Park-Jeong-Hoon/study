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

<br>배열 초기화
```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] //정수형 데이터를 담는 배열
console.log(numbers); //배열 요소를 모두 출력하려면 이렇게
```

```javascript
const sports = ["baseball", "soccer", "volleyball", "basketball"]; //String형 데이터를 담는 배열
```

```javascript
const arr = [29, 14.62, "great", true]; //다양한 타입의 데이터를 담을 수도 있다.
```

```javascript
const num = 47;
const arr = [29, 14.62, "great", true, num] //이렇게 num 같이 초기화된 변수를 넣어도 된다.
```
