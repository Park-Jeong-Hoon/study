># JavaScript 공부 정리
## <br>html파일에 JavaScript파일 추가하기
```html
<body>
    Hello world!!
    <script src="index.js"></script> <!--자바스크립트 파일명.js-->
</body>
```


## <br><br> 변수 초기화
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
var -> 재선언O, 재할당O<br><br>
typeof를 이용하면 변수에 어떤 타입의 값이 들어있는지 알 수가 있다.
```javascript
const a = 29;
const b = 14.62;
const c = "great";
const d = true;

console.log(typeof a); //number
console.log(typeof b); //number
console.log(typeof c); //string
console.log(typeof d); //boolean
```

## <br><br>배열
```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] //정수형 데이터를 담는 배열
console.log(numbers); //배열 요소를 모두 출력하려면 이렇게
numbers.push(11); //배열에 새로운 항목 추가도 가능
console.log(numbers[0]); //접근은 이렇게한다. (왼쪽의 결과는 1)
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

## <br><br>객체
<br>객체 생성&출력
```javascript
const kimInfo = { //이렇게 객체를 만든다.
    name: "Kim",  //안에는 속성들이 있다.
    age: 29,
    gender: "Male"
}

console.log(kimInfo); //객체를 한번에 출력
```

<br>객체의 속성 접근&수정&추가
```javascript
const kimInfo = {
    name: "Kim",
    age: 29,
    gender: "Male"
}

console.log(kimInfo.age); //객체에서 원하는 속성값 접근 방법1
console.log(kimInfo["age"]); //객체에서 원하는 속성값 접근 방법2

kimInfo.age = 30; //객체가 const이지만 그 안에 있는 속성의 값을 변경 가능, 객체 자체는 변경 못함
kimInfo.nationality = "Korea"; //이렇게 새로운 속성을 추가할 수도 있다.

console.log(kimInfo.age); //객체의 원하는 속성값만 출력
```

<br>객체 속 배열&객체
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
console.log()에서 console 역시 객체이고 log는 console이라는 객체가 가지고 있는 함수이다.

## <br><br>함수
<br>함수 작성 방법
```javascript
//함수는 이렇게 작성
function func() {
    console.log("This is funcion");
}

func(); //이렇게 함수를 호출하면 함수 기능 수행
```

<br>매개변수 있는 함수
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

<br>함수 안에서 되도록 결과값 반환하도록
```javascript
function func(a, b) {
    return `Hello ${a} you are ${b} years old`;
} //이렇게 함수 안에서 값을 반환해서

const result = func("Man", 25); //함수의 결과 값을 이용하는 것이 좋다.

console.log(result);
```

<br>객체 안의 함수
```javascript
const cal = { //계산 기능을 가진 객체
    //객체 안에서 함수를 만들 때에는 아래와 같이 '함수명:function(인자){함수내용}' 형식으로 작성한다.
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
<br>*forEach*<br>
forEach를 이용하면 한 배열에 대해 배열의 모든 요소에 대해 각각 같은 함수를 실행할 수가 있다.
```javascript
function func() {
    console.log("Hello");
}

const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

numbers.forEach(func); //numbers배열의 요소 개수만큼 "Hello" 가 출력됨.
```

<br>forEach안에 들어가는 함수의 첫번째 인자는 배열의 각 요소이다. 즉, 아래 코드에서 func함수의 인자로 item이 있는데 이 item은 forEach로 배열의 각 요소마다 함수를 실행시켜 줄 때 각 요소(아래 함수에서는 a, b, c)를 의미하는 것이다. 따라서 아래 함수를 실행시키면 배열의 모든 요소 a, b, c에 대해 함수가 실행되기 때문에"Hello a", "Hello b", "Hello c"가 된다.
```javascript
function func(item) {
    console.log("Hello " + item);
}

const arr = ["a", "b", "c"];

arr.forEach(func);
```

<br>*arrow function*<br>
또한 위의 코드는 아래와 같이 arrow function을 이용해서 별도의 함수를 만들 필요 없이 더욱 간단히 구현할 수가 있다.
```javascript
const arr = ["a", "b", "c"];

arr.forEach((item) => console.log("Hello " + item));
```

<br>*Math모듈의 random함수*<br>
javascript에서는 random함수를 이용해서 난수를 생성할 수 있다. random함수를 이용하면 0과 1사이의 수를 랜덤할 수가 있다. 또한 이를 응용해서 더욱 다양한 범위의 값들을 나타낼 수 있다.
```javascript
console.log(Math.random()); //0~1사이의 난수
console.log(Math.random() * 10); //0~10 사이의 난수
```

또한 ceil, round, floor 함수를 이용해서 숫자의 소수점 아래 부분을 올림(ceil), 반올림(round), 버림(floor)하여 정수 형태로 나타낼 수 있다.
```javascript
console.log(Math.ceil(10.3)); //올림 결과:11
console.log(Math.round(10.3)); //반올림 결과:10
console.log(Math.floor(10.3)); //버림 결과:10
```

## <br><br>DOM(Document Object Model)<br>
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

html파일의 실행결과로 Hello world!!라는 문장이 아닌 Hi라는 문장이 나온다. 이는 자바스크립트에서 document.getElementById를 통해 HTML파일에서 Id가 hello인 element를 가져와서 ex에 저장한 다음 ex에서 innerHTML을 통해 Hello world!!를 Hi라고 변경해준 것이다. 즉, document라는 객체가 자바스크립트와 HTML을 서로 이어주는 역할을 하는 것으로 자바스크립트에서는 document객체를 이용해 HTML파일의 원하는 element를 불러오고 추가하고 또 element의 항목까지 수정할 수가 있다. 또한 className으로 찾고 싶으면 getElementsByClassName, name으로 찾고 싶으면 getElementsByName 그리고 아래와 같이 querySelector을 이용해서 css에서의 표현처럼 id, class 등 html의 모든 element들을 대상으로 찾아서 원하는대로 바꿔줄 수도 있다.

```javascript
const ex = document.querySelector("#hello");
ex.innerHTML = "Hi";
ex.style.color = "red";
document.title = "wow";
```

getElemntById를 이용하면 Id로만 찾을 수 있지만 querySelector을 이용하면 보다 많은 선택자를 이용해 찾을 수 있다는 점에서 더욱 편리하고 유용한 것 같다. 그런데 querySelector을 이용할 경우 selector 안의 조건에 부합하는 여러 element들이 있을 때 그 중 가장 첫번째 element만 가져온다는 특징이 있다. 따라서 조건에 부합하는 모든 element들을 가져오고 싶은 경우에는 querySelectorAll을 이용하면 된다.<br><br>
querySelector은 다양한 방법으로 사용할 수 있는데 그 중 크게 몇가지를 예시로 들어보면 아래와 같다.<br>

<br>ex1) 선택자 하나만 이용해서 찾기
```javascript
const ex = document.querySelector("#hello");
```

<br>ex2) 부모 태그 안에 여러개의 자식 태그들이 있을 때 특정 태그를 선택하고 싶을 때
```javascript
const ex = document.querySelector("h1 #hello"); //선택자 사이에 공백이 들어간다.
```

<br>ex3) 같은 이름의 태그가 여러개 있고 각자 id나 class명이 다를 때 특정 태그를 선택하고 싶을 때
```javascript
const ex = document.querySelector("h1#hello"); //선택자 사이에 공백이 없다.
```

<br> *createElement*
<br>자바스크립트에서는 위처럼 HTML파일에 있는 element를 가져올 수도 있지만 새로운 element를 만들어서 HTML파일에 추가해줄 수도 있다. 그 때 사용하는 것이 바로 createElement이다. 
```javascript
const htag = document.createElement("h"); //h 태그를 생성한다.
document.body.appendChild(htag); //body에 h태그를 추가해준다.
```


## <br><br>이벤트 & 이벤트 핸들러
보통 함수를 호출할 때 함수 이름이 func라면 func()라고 호출을 하는데 이벤트 핸들러 함수의 경우에는 func라고 호출한다. 왜냐하면 func()는 함수를 즉시 호출한다는 의미이고 func는 함수를 필요한시점에, 즉 아래 코드에서는 window.addEventListener("resize", func)의 경우에는 화면에 변화를 주는 시점에만 호출을 한다는 의미이다. 만약 이 부분에서 func를 func()로 바꿔주고 콘솔창을 보면 웹페이지를 처음 열었을 때만 func함수가 호출되고 사이즈의 변화를 줄 때는 정작 호출이 안된다. 하지만 func()로 바꿔주면 사이즈의 변화를 줄 때만 호출이 된다.
```javascript
const ex = document.querySelector("#hello");

function func() {
    console.log("resize event")
}

window.addEventListener("resize", func());
```

위의 HTML파일과 아래의 JavaScript파일을 같이 이용하면 Id가 hello인 부분 즉, 여기서는 Hello world!!부분을 클릭할 때마다 이벤트가 발생한다. 또한 아래의 코드에서 isClicked함수의 매개변수로 event가 있는데 이와 같이 모든 이벤트리스너 함수의 첫번째 인자(명칭은 아무렇게 해도 상관없으나 관례상 event라고 많이 씀)로는 이벤트가 발생하면서 생긴 정보들이 담겨지게 된다. 이벤트리스너 함수의 첫번째 인자는 필요하다면 아래와 같이 작성해주면 되고 필요가 없다면 굳이 작성해주지 않아도 된다.
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
JavasCript에는 click 외에도 다양한 이벤트들이 있는데 무슨 이벤트가 있는지 알고 싶으면 https://developer.mozilla.org/ko/docs/Web/Events 로 가면 된다. 또는 console.dir(document); 라는 코드를 작성해서 콘솔창에서 나오는 결과를 펼친다음 on으로 시작하는 이벤트들을 쭉 볼 수가 있다. <br>
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
