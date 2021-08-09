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
const a = 29; //Integer
const b = 14.62; //Float
const c = "great"; //String
const d = true; //Boolean
```
let -> 재선언X, 재할당O<br>
const -> 재선언X, 재할당X<br>
var -> 재선언O, 재할당O<br>

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

html파일의 실행결과로 Hello world!!라는 문장이 아닌 Hi라는 문장이 나온다. 이는 자바스크립트에서 document.getElementById를 통해 HTML파일에서 Id가 hello인 요소를 가져와서 ex에 저장한 다음 ex에서 innerHTML을 통해 Hello world!!를 Hi라고 변경해준 것이다. 또한 아래와 같이 querySelector을 이용해서
css에서의 표현처럼 id, class 등 html의 모든 요소들을 대상으로 찾아서 원하는대로 바꿔줄 수도 있다.

```javascript
const ex = document.querySelector("#hello");
ex.innerHTML = "Hi";
ex.style.color = "red";
document.title = "wow";
```

getElemntById를 이용하면 Id로만 찾을 수 있지만 querySelctor을 이용하면 보다 많은 선택자를 이용해 찾을 수 있다는 점에서 더욱 편리하고 유용한 것 같다.


## <br>이벤트 & 이벤트 핸들러
보통 함수를 호출할 때 함수 이름이 func라면 func()라고 호출을 하는데 이벤트 핸들러 함수의 경우에는 func라고 호출한다. 왜냐하면 func()는 함수를 즉시 호출한다는 의미이고 func는 함수를 필요한시점에, 즉 아래 코드에서는 window.addEventListener("resize", func)의 경우에는 화면에 변화를 주는 시점에만 호출을 한다는 의미이다. 만약 이 부분에서 func를 func()로 바꿔주고 콘솔창을 보면 웹페이지를 처음 열었을 때만 func함수가 호출되고 사이즈의 변화를 줄 때는 정작 호출이 안된다. 하지만 func()로 바꿔주면 사이즈의 변화를 줄 때만 호출이 된다.
```javascript
const ex = document.querySelector("#hello");

function func() {
    console.log("resize event")
}

window.addEventListener("resize", func());
```

위의 HTML파일과 아래의 JavaScript파일을 같이 이용하면 Id가 hello인 부분 즉, 여기서는 Hello world!!부분을 클릭할 때마다 이벤트가 발생한다.
```javascript
const ex = document.querySelector("#hello");

function isClicked(event) {
    console.log(event)
}

ex.addEventListener("click", isClicked);
```


조건문을 이용하면 보다 다양한 이벤트 처리를 할 수가 있다. 아래의 코드를 위의 HTML파일과 함께 이용해서 실행하면 Hello world!! 부분을 클릭할 때마다 색깔이 계속 변화한다.
참고로 자바스크립트의 비교연산자에서 주목할 부분이 있는데 바로 ==과 ===이다. ==은 값만 비교하지만 ===은 값과 타입을 모두 비교한다. 예를 들면 1 == "1" 의 결과는 true이고 1 === "1" 의 결과는 false이다. 마찬가지로 같지 않은지를 비교할 때는 값만 비교하는 !=, 값과 타입 모두 비교하는 !==를 이용한다.
```javascript
const ex = document.querySelector("#hello");

const colorOne = "rgb(255, 0, 0)"; //color을 표기할 때 이렇게 안하고 #3498db같은 식으로 하면 비교연산할 때 잘 되지 않는다.
const colorTwo = "rgb(0, 0, 255)";

function isClick() {
    const colorNow = ex.style.color;
    if(colorNow === colorOne) {
        ex.style.color = colorTwo;
    } else {
        ex.style.color = colorOne;
    }
}

function init() {
    ex.style.color = colorOne;
    ex.addEventListener("click", isClick);
    //ex.addEventListener("mouseenter", isClick); //mouseenter이벤트로 하면 클릭이 아니라 마우스가 텍스트 안에 들어갈 때마다 색이 바뀐다.
}

init();
```
JavasCript에는 click 외에도 다양한 이벤트들이 있는데 무슨 이벤트가 있는지 알고 싶으면 https://developer.mozilla.org/ko/docs/Web/Events 로 가면 된다.<br>
지금까지 JavaScript코드를 보면 HTML, CSS에서 할 일까지 너무 다하고 있는데 이건 그렇게 좋지 않은 방식이다. JavaScript에서는 로직을 처리하게 하는 것이 좋다.

CSS파일을 이렇게 만들어 주고
```css
body {
    background-color: #ecf0f1;
}

h1 {
    color: #3498db;
}

.clicked {
    color: #8e44ad;
}
```

JavaScript파일을 이렇게 만든다.
```javascript
const ex = document.querySelector("#hello");

const clikedClass = "clicked";

function isClicked() {
    const classNow = ex.className;
    if(classNow == clikedClass) { //클래스명이 css파일의 clicked와 같으면 클래스명 ""로
        ex.className = "";
    } else {
        ex.className = clikedClass; //다르면 clicked로 클래스명 설정
    }
}

function init() {
    ex.addEventListener("click", isClicked);
}

init();
```
이렇게 되면 처음에 클릭을 했을 때 hello 아이디로 가져온 ex에는 클래스이름이 없어서 JavaScript파일에서 isClicked함수에서 클래스이름이 없으니까 else문으로 가고 CSS파일에서 설정된 clicked클래스의 속성들이 적용되면서 색이 변하고 그 다음에는 클래스이름이 clicked이므로 if문으로 가서 클래스네임이 ""로 바뀌면서 clicked클래스의 속성들이 적용되었던게 지워지면서 이전의 색으로 바뀌게 된다. 그런데 이렇게 코드를 짜면 문제가 발생하는 경우가 있다. 조금더 코드를 추가해본다.<br>

HTML코드에 h1태그에 클래스네임을 지정한다.
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Something</title>
    <link rel="stylesheet" href="index.css" />
</head>
<body>
    <h1 id="hello" class="hi">Hello world!!</h1> <!-- 클래스명 "hi" -->
    <script src="index.js"></script> <!--자바스크립트 파일명.js-->
</body>
</html>
```

CSS코드에 앞에서 만든 hi클래스의 속성을 설정한다.
```css
body {
    background-color: #ecf0f1;
}

h1 {
    color: #3498db;
    transition: color 0.5s ease-in-out;
}

.clicked {
    color: #8e44ad;
}

.hi {
    cursor: pointer;
}
```
JavaScript 파일은 그대로 놔두고 실행을 하면 마우스로 텍스트에 갖다댔을 때 처음에는 커서가 손모양으로 바뀌지만 한번 클릭한 이후로는 클래스명이 바뀌어버리기 때문에 커서가 손모양으로 더이상 발생하지 않는다. 이를 해결하기 위해서는 classList를 사용할 수가 있다.

```javascript
const ex = document.querySelector("#hello");

const clikedClass = "clicked";

function isClicked() {
    const hasClicked = ex.classList.contains(clikedClass);
    if(hasClicked) { //classList에 "clicked"가 포함되어있으면 그것을 제거
        ex.classList.remove(clikedClass);
    } else {
        ex.classList.add(clikedClass); //아니면 그것을 추가
    }
}

function init() {
    ex.addEventListener("click", isClicked);
}

init();
```
JavaScript 코드를 이렇게 수정하면 위의 문제가 해결된다. 놀라운점은 여기서 좀 더 개선을 할 수가 있다는 점이다. 바로 toggle을 이용해서 말이다. 위의 코드를 보면 isClicked함수가 조금 길다. 그런데 toggle이라는 함수는 어떤 클래스가 클래스리스트에 있는지 체크해서 있으면 remove, 없으면 add를 해주는 함수라서 코드의 길이를 확 줄일 수가 있다. 아래 코드처럼 수정하면 코드의 길이는 훨씬 줄고 결과는 같게 나온다.

```javascript
const ex = document.querySelector("#hello");

const clikedClass = "clicked";

function isClicked() {
    const hasClicked = ex.classList.toggle(clikedClass);
}

function init() {
    ex.addEventListener("click", isClicked);
}

init();
```
