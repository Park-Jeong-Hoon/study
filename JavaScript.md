># JavaScript 공부 정리
## html파일에 JavaScript파일 추가하기<br>
```html
<body>
    Hello world!!
    <script src="index.js"></script> <!--자바스크립트 파일명.js-->
</body>
```


## <br> 변수 초기화
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

## <br>배열
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

## <br>객체
```javascript
const kimInfo = { //이렇게 객체를 만든다.
    name: "Kim",
    age: 29,
    gender: "Male"
}

console.log(kimInfo); //객체를 한번에 출력
```

```javascript
const kimInfo = { //이렇게 객체를 만든다.
    name: "Kim",
    age: 29,
    gender: "Male"
}

console.log(kimInfo.age); //객체에서 원하는 값 접근 가능

kimInfo.age = 30; //객체가 const이지만 그 안의 값을 변경 가능, 객체 자체는 변경 못함

console.log(kimInfo.age);
```

```javascript
const davidInfo = {
    name: "David",
    age: 25,
    job: "Developer",
    hobby: ["Playing game", "Watching movie",
    "Reading book"], //객체 안에 배열을 담을 수 있음
    favSports: [
        { //배열 안에 객체를 담을 수 있음
            name:"Baseball",
            isWithBall:true
        },
        {
            name:"Swimming",
            isWithBall:false
        }
    ]
}
```
console.log()에서 console 역시 객체이고 log는 console이라는 객체가 가지고 있는 함수이다.<br><br>

## 함수
```javascript
//함수는 이렇게 작성
function func() {
    console.log("This is funcion");
}

func(); //이렇게 함수를 호출하면 함수 기능 수행
```

```javascript
//매개변수 있는 함수
function func(what) {
    console.log("This is funcion", what);
}

func(1); //함수 호출시 함수에 필요한 인자 넣어줌
```

```javascript
//여러개의, 다양한 타입의 매개변수 받을 수 있음
function func(a, b) {
    console.log("This is funcion", a, " Hello ", b);
}

func(1, "Man");
```

```javascript
//여러개의, 다양한 타입의 매개변수 받을 수 있음
function func(a, b) {
    console.log('Hello ' + a + " you are " + b + " years old");
} //JavaScript에서는 "", '' 모두 String 형이다.

func("Man", 25);
```

```javascript
function func(a, b) {
    console.log(`Hello ${a} you are ${b} years old`);
} //JavaScript에서는 String을 위와 같이 표현할 수도 있다. (``로 감싸주고 ${변수명})

func("Man", 25);
```

```javascript
function func(a, b) {
    return `Hello ${a} you are ${b} years old`;
} //이렇게 함수 안에서 값을 반환해서

const result = func("Man", 25); //함수의 결과 값을 이용하는 것이 좋다.

console.log(result);
```

```javascript
const cal = { //계산 기능을 가진 객체
    plus: function(n, m) { //덧셈 함수
        return n + m;
    },
    minus: function(n, m) { //뻴셈 함수
        return n - m;
    },
    multiply: function(n, m) { //곱셈 함수
        return n * m;
    },
    divide: function(n, m) { //덧셈 함수
        return n / m;
    }
}

const plusResult = cal.plus(10, 5); //객체의 함수를 접근해서 결과를 받아옴
const minusResult = cal.minus(10, 5);
const mulResult = cal.multiply(10, 5);
const divResult = cal.divide(10, 5);

console.log(plusResult);
console.log(minusResult);
console.log(mulResult);
console.log(divResult);
```

## <br>DOM(Document Object Model)<br>
JavaScript는 HTML과 함께 쓰일 수 있다. HTML파일과 JavaScript파일이 각각 아래와 같다고 할 때<br>

HTML파일
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Something</title>
    <link rel="stylesheet" href="index.css" />
</head>
<body>
    <h1 id="hello">Hello world!!</h1>
    <script src="index.js"></script> <!--자바스크립트 파일명.js-->
</body>
</html>
```

JavaScript파일
```JavaScript
const ex = document.getElementById("hello");

ex.innerHTML = "Hi";
```

html파일의 실행결과로 Hello world!!라는 문장이 아닌 Hi라는 문장이 나온다. 이는 자바스크립트에서 document.getElementById를 통해 HTML파일에서 Id가 hello인 요소를 가져와서 ex에 저장한 다음 ex에서 innerHTML을 통해 Hello world!!를 Hi라고 변경해준 것이다.
