># NodeJS 공부 정리
## <br>NodeJS란?
- 자바스크립트 런타임
- 브라우저 밖에서 돌아가는 자바스크립트

## <br>npm
- 자바스크립트 언어를 위한 패키지 매니저
- NodeJS와 같이 쓰이고 NodeJS와 상호작용 할 수 있게 해줌
- NodeJS를 설치하면 같이 설치됨
- npm을 이용해 다른 사람들이 만든 패키지를 쓸 수 있음. ```npm install (패키지명)``` 또는 ```npm i (패키지명)``` 이라는 명령어로 원하는 패키지를 다운받을 수 있다.

## <br>package.json
- NodeJS 프로젝트를 할 때 가장 먼저 만들어야하는 파일로 package.json이라는 이름으로 생성해야 한다.
- 직접 만들기 보다는 npm 명령어를 이용해서 만든다.
- 만들 때 명령어
  1. ```npm init```
  2. package name, version, description, entry point, test command, git repository, keywords, author, license 확인 또는 작성 후 엔터
  3. package.json 생성됨
- 생성한 package.json 파일은 원하는대로 수정해도 된다.
- main은 프로젝트의 대표파일로 package를 배포했을 때 다른 사람이 main으로 되있는 파일을 사용하게 된다. 파일명이 index.js라 할 때 명령창에 node index.js 라고 치면 실행 시킬 수 있다. 그런데 main파일은 필수가 아니라 생략해도 된다.
- scripts는 또다른 방법으로 파일을 실행하게 해준다. ```"scripts": {"dev": "node index.js"}```일 때 명령창에 ```npm run dev``` 라고 치면 index.js 파일을 실행할 수 있다. 물론 명령어는 프로젝트 폴더 안에서 쳐야 한다. 폴더 밖이나 package.json이 없는 폴더에서 명령어를 치면 실행할 수 없다.

## <br>express
- 서버를 만드는데 필요한 패키지
- 명령창에 ```npm i express``` 또는 ```npm install express```를 쳐서 express를 다운 받을 수 있다.
- 다운 받기 전에는 package.json 파일을 비롯해 열려있는 파일들을 저장한다.
- 다운을 받고 난 후
  - node_modules와 package-lock.json 파일이 생성된다.
  - node_modules에는 express 외에 다른 필요한 패키지들도 있다.
    - express안에도 package.json파일이 있고 이 안에는 scripts, contributers, dependencies 등이 있다. dependencies는 express가 작동되려면 필요한 패키지들이다.
    - npm install express를 실행하면 express를 다운 받으면서 express의 dependencies도 같이 다운 받는다. 즉 express를 설치하면서 express가 의존하는 패키지를 같이 설치하고 express가 의존하는 패키지들을 설치하면서 이들이 의존하는 패키지도 같이 설치하는 것이다. 이 모든 것들을 npm이 해준다.
  - 기존에 만들었던 package.json 파일에 dependencies로 express가 생긴다. 이 역시 npm이 해주는 것이다.
  - package-lock.json은 패키지들을 안전하게 관리해준다. 즉 다른 사람이 프로젝트를 받아 ```npm i``` 명령어를 쳤을 때 그 사람도 같은 버전의 모듈을 설치할 수 있게 된다.
- 참고로 package.json에서 express dependencies가 존재한다면 ```npm i```만 쳐도 node_modules와 package-lock.json 파일이 설치되면서 node_modules안에는 express와 express가 의존하는 패키지들이 들어있도록 설치가 된다. 이것 역시 npm이 package.json파일에서 dependencies를 보고 그 안에 있는 모듈들을 알아서 설치하는 것이다.
- ```npm i``` 명령어만 치면 npm이 package.json파일의 dependencies를 보고 필요한 모듈들을 알아서 설치해주므로 용량이 큰 node_modules는 깃허브에 올리지 않아도 된다. 깃허브에 안올리려면 .gitignore 파일을 만든 다음 ```/node_modules```라고 치면 된다.

## <br>Babel
- 작성한 자바스크립트 코드를 NodeJS가 이해할 수 있는 자바스크립트로 바꾸는 것이다.
- ```npm install --save-dev @babel/core``` 명령어를 이용해서 설치할 수 있다.
- 설치한 후
  - package.json을 열어보면 devDependencies안에 @babel/core가 들어가 있는 것을 볼 수가 있다.
  - 그냥 dependencies는 프로젝트에 필요한 것들을 나타내고 devDependencies는 개발자(사람)에게 필요한 dependencies이다.
  - 프로젝트에 express가 필요하기 때문에 dependencies에 express가 들어가고 개발자가 최신 문법의 코드를 작성하려면 babel이 필요하기 때문에 devDependencies에 babel이 들어간다.
  - package.json은 텍스트 파일로 dependencies나 devDependencies같은 구분은 어떤 패키지가 무슨 역할을 하는지 알 수 있도록 사람을 위한 것이다. 어차피 node_modules안에 필요한 것들이 설치가 되어있다.
  - 참고로 babel을 설치 할 때 ```--save-dev```를 사용했기에 babel이 devDependencies에 들어간 것이고 이를 사용하지 않으면 dependencies에 들어간다. 하지만 그렇다 해도 package.json을 수정해주면 되므로 상관없다.
  - 설치완료 후에는 babel.config.json이라는 설정 파일을 만들어주고 ```npm install @babel/preset-env --save-dev``` 명령어를 쳐서 devDependencies에 @babel/preset-env가 들어온지 본 다음 babel.config.json파일에 ```{"presets": ["@babel/preset-env"]}``` 라는 코드를 작성한다.
    - preset은 babel을 위한 거대한 플러그인이다. preset-env는 그 중 하나이며 이를 이용하면 최신 자바스크립트 구문을 사용할 수가 있다.
  - 그 다음에는 ```npm install @babel/node --save/dev``` 명령어를 쳐서 @babel/node를 설치한다.
  - 그 다음에는 package.js에서 scripts를 ```"dev": "babel-node index.js"```로 수정한다.
  - 그리고 나서 명령창에 ```npm run dev```라고 치면 정상 작동한다. 그런데 파일을 수정 할 때마다 이 명령어를 쳐야한다는 번거로움이 있다. 이를 해결하기 위해서 사용하는 것이 nodemon이다. ```npm install nodemon --save-dev``` 명령어를 쳐서 nodemon을 설치한다. nodemon은 개발자가 수정하는 것을 알아차린다. 이렇게 되면 개발자는 파일을 수정한 후 굳이 ```npm run dev``` 명령어를 칠 필요가 없다.
  - nodemon을 설치하고 나서 package.js파일에서 scripts를 ```"dev": "nodemon --exec babel-node index.js"```로 수정한다.
  - 그 다음 ```npm run dev``` 명령어를 치면 실행이 되고 콘솔 창이 종료되지 않는다. 그 이후로 파일을 수정할 때마다 알아서 실행이 된다. 종료를 하려면 ```ctrl+c```를 누르면 된다.


## <br>서버
- 서버는 request를 기다리고 응답한다.
- 위에서 setup이 종료되면 이제 JS파일에 신경을 써야 한다. express를 import하려면 ```import express from "express"; ``` 라고 하면 된다. 이는 express 패키지를 express라는 이름으로 import 한다는 의미이다. express application을 만드려면 ```const app = express()``` 라는 코드를 작성해주면 된다.
- ```app.listen(4000, func(함수명))``` 라고 코드를 작성하면 서버가 4000port를 listening 하게 되고 함수가 구현이 되있으면 서버를 만들게 되는 것이다.
- application 설정에 관한 코드는 application을 만든코드 ```const app = express()``` 와 외부 접속을 listen하는 코드 ```app.listen(4000, func(함수명))``` 사이에 작성을 해야 한다.
- /은 서버의 root, 첫 페이지이다.
- GET은 HTTP method로 유저가 원하는 페이지를 갖다 달라고 부탁하는 것이다.
- ```app.get("/", func(함수명))``` 코드는 유저가 root page로 get request를 보내면 func라는 함수로 답하는 것이다.
- ```app.get("/", func(함수명))``` 에서 func에는 request, response 객체가 있다. 즉 ``` const func = (request, response) => {함수내용} ``` 이다.
  - ```{함수내용}```에서 ```response.end()``` 를 해주면 서버가 request를 끝내도록 하고 ```res.send("bye")``` 를 해주면 메시지를 화면에 나타내면서 request를 끝낼 수 있다.

## <br> 미들웨어
- request와 response 사이에 있는 소프트웨어
- 모든 controller은 미들웨어가 될 수 있다.
- ```app.get("/", one(함수명1), two(함수명2))``` 에서 one이 미들웨어, two는 파이널웨어가 되는 것이다.
  - 서버 설명에서 ```app.get("/", func(함수명))``` 에서 func에는 request, response 객체가 있다고 했는데 여기에 next까지 있다. 그런데 파이널웨어인 경우에는 next가 굳이 필요가 없는 것이고 미들웨어인 경우에는 ``` const one = (request, response, next) => {함수내용} ``` 같은 형태로 사용해주면 된다.
  - one에서 next를 이용해야 미들웨어가 되면서 one의 다음 함수인 two가 호출이 되고 이용하지 않는다면 파이널웨어가 되버려 two가 호출되지 않는다.
  - 이렇게 get을 이용하면 미들웨어가 위에서 지정한 "/" route에만 적용이 된다.
- ```app.use(middlefunc(미들웨어로 사용할 함수 명))``` 이 코드를 모든 get 보다 위에 작성해주면 모든 route에 미들웨어가 적용이 된다.

## <br> morgan
- node.js 용 request logger middleware
- ```npm i morgan``` 명령어를 이용해 설치한다.
- 사용방법
  1. ```import morgan from "morgan";``` 코드를 작성해서 morgan 패키지를 import한다.
  2. ```app.use(morgan("dev"));``` 코드를 작성하면 앞에서 직접 만들었던 미들웨어 함수같이 동작하는데 더 섬세하게 동작한다.
- morgan 역시 next가 있다.

## <br> Router
- 라우터는 작업중인 주제를 기반으로 URL을 그룹화해준다.
  - 공통 시작 부분을 기반으로 url을 정리해주는 것이다.
- 사용방법
  1. ```const globalRouter = express.Router();```, ```const menuRouter = express.Router();``` 와 같은 코드를 작성하면 라우터를 만들 수 있다.
  2. ```app.use("/", globalRouter);```, ```app.use("/menu", globalRouter);``` 와 같은 코드를 작성하면 라우터를 사용할 수 있게 된다.
  3. ```globalRouter.get("/", func1(함수명));``` 코드를 작성하면 "/"에 접속했을 때 func1를 이용해 응답을 해준다.
  4. ```menuRouter.get("/goods", func2(함수명));``` 코드를 작성하면 "/menu/goods"에 접속했을 때 func2를 이용해 응답을 해준다.
  5. routes에 ```/:id``` 를 적어주면 변수 역할을 해준다. 즉 ```id```가 변수인 것이고 이는 어떤 명칭이라도 상관없다. ```:```만 적어주면 된다. 또한 ```/:id(\\d+)``` 이렇게 적어주면 변수값으로 숫자만 받게 된다.

## <br> Export
- 개발을 할 때 코드를 클린하게 하는 것이 좋다. 따라서 비슷한 성격의 코드끼리 묶어서 모듈화시켜주는 것이 좋다. 그러러면 폴더를 따로 만들어서 그 안에 js파일들을 넣어주면 된다. 그런데 이렇게 모듈화 한 파일 속 변수를 다른 파일에서 이용하려면 어떻게 해야 할까 바로 import를 해야 한다. 그런데 그 전에 import하려는 변수를 export 해줘야 한다.
- export를 하는 방법
  1. ```export default + 변수명``` 한 다음 사용하려는 파일에서 ```import 변수명 from 원래 변수가 있는 경로```
     - 이렇게 하면 파일에 있는 다양한 변수 중 하나의 변수만 다른 파일로 imoprt 할 수 있다.
  2. 변수를 선언하는 곳에서 변수 앞에 ```export``` 붙인 후 가져다 쓰려는 파일에서 ```import {변수명} from 원래 변수가 있는 경로```
     - 이렇게 하면 한 파일에 있는 다양한 변수를 다른 파일로 import 할 수 있다.

## <br> PUG
- html을 리턴하려면 Controller에서 respond.send안에 html코드를 작성해서 리턴해줄 수 있다. 하지만 이렇게 하면 너무 작업이 번거로워지고 수정하기도 힘들다. 따라서 html을 좀 더 간편하게 리턴해주기 위해 사용하는 것이 PUG라는 템플릿 엔진이다.
- 사용방법
  1. ```npm i pug``` 명령어를 이용해 설치한다.
  2. ```app.set("view engine", "pug");``` 코드를 작성해서 뷰엔진을 pug로 설정한다.
  3. pug 파일을 생성해 원하는 내용을 작성한다.
  4. pug 파일에서 JS코드나 변수 등을 작성하고 싶으면 ```#{}```을 이용해서 이 안에다 적으면 된다. 특이한 점이 있는데 pug에서는 예를 들어 li 태그 안에 텍스트와 변수를 같이 넣고 싶으면 ```li 내용 #{변수}``` 형태로 적어주면 되고 변수만 넣고 싶으면 ```li=변수``` 형태로 적어주면 된다. 하지만 href 같이 속성값에 변수를 작성하고 싶으면 JS에서 처럼 ``` `내용 ${}` ``` 형태로 작성하거나 ``` "내용" + 변수 ``` 형태로 작성하면 된다.
  5. Controller에서 ```respond.render(pug파일명)``` 코드 같이 respond 객체의 render을 이용해 pug파일을 렌더링 해준다.
- 코드 작성방법
  - html파일과 비슷하지만 더 간단하게 작성할 수 있다. ```<body></body>``` 와 같이 html에서 태그를 열고 닫아줘야 하는 것에 비해 pug에서는 태그를 작성하고 옆에 한칸 띄우고 내용을 작성하고 자식 태그를 넣고 싶다면 tab을 누른 다음 작성하고 따로 닫아줄 필요가 없다.
  - Partials
    - footer와 같이 여러 페이지에 동일하게 적용되는 부분을 페이지마다 작성하기는 너무 번거롭다. 따라서 이런 경우에는 따로 파일을 만들어 내용을 작성하고 이 내용을 적용하고 싶은 페이지의 pug파일에 ```include 파일명``` 라고 해주면 된다. 파일명을 적을 때 경로를 잘 적어줘야 한다.

## <br> extends
- 위에서 footer같이 동일한 내용을 여러번 작성하는 것이 번거롭다고 했듯이 동일하지 않더라도 거의 비슷한 내용의 PUG파일을 여러번 작성하는 것은 낭비다. 따라서 사용하는 것이 extends이다. 
- 여러 페이지에 비슷한 부분이 들어가는 경우 대표적으로 사용할 pug파일(예를 들어 파일명을 base로)을 하나 만들어 내용을 작성해주고 이를 적용하고 싶은 pug파일에 ```extends base.pug``` 라고 작성해주면 된다. 이렇게 하면 base의 내용이 똑같이 적용되게 된다. 그런데 base의 내용 중 일부를 변경하고 싶다면 base.pug에서 ```block```을 이용해 base.pug를 extends한 파일에서 이 부분을 채워넣게 하면 된다. 예를 들어 base.pug에서 ```block content``` 라고 하면 base.pug를 extends한 파일에서는 ```block content```를 작성한 다음 그 다음 줄에서 tab을 하고 원하는 pug코드를 작성하면 되는 것이다.
- ```#{}``` 을 사용하면 extends한 내용에서 block 보다 더 세세한 부분까지 변경할 수 있다. 즉 예를 들어 base.pug에 ```h1 I love fruits``` 라는 부분이 있는데 이를 extends한 어느 파일에서 fruits 부분을 apple로 바꾸고 싶을 수가 있다. 이럴 경우에 base.pug에서 ```h1 I love ${변수명}```이라 작성하고 extends한 파일을 렌더링 하는 컨트롤러에서 ```res.render("extends한 파일명", {변수명:"apple"})``` 이렇게 작성해주면 된다.(res는 respond 객체)

## <br> Mixin
- Partial을 이용하면 똑같은 코드를 여러번 쓰지 않아도 된다는 장점이 있지만 너무 똑같기만 한게 단점이 될 수가 있다. 따라서 전체적인 구조는 같지만 페이지마다 다른 요소를 집어넣어 보여주고 싶을 때 사용하는 것이 mixin이다. 쉽게 말해 매개변수가 있는 partial라고 표현하면 된다.
- 사용방법
  1. mixin으로 사용할 파일을 생성하고 맨 위에 ```mixin hi(n)``` 코드를 작성한다.(여기서 hi는 mixin의 이름, n은 매개변수) 그러고 매개변수를 이용해서 원하는 pug코드를 작성한다.
  2. 적용하고 싶은 pug파일에다가 ```include 경로/video``` 를 하고 mixin을 이용하고 싶은 위치에 ```+hi(n)``` 코드를 작성한다.(여기서 hi는 mixin의 이름이며 앞에 +를 꼭 붙여야 하고 n은 인자이며 hi에서 사용하는 매개변수에 알맞게 넣어줘야 한다.)

## <br> GET, POST
- 폼을 전달할 때 method로 GET, POST 두 가지 방식이 있다.
- defalut 값으로는 GET으로 되어 있다.
- 특징
  - GET
    - 검색을 할 때 사용되며 검색어가 주소창에 포함되어 action으로 설정된 페이지로 전달된다.
  - POST
    - 파일을 보내거나 데이터베이스에 있는 값을 바꿀 때, 로그인을 할 때 사용한다.
- 라우터에서의 사용
  - GET
    - ```라우터명.get("경로", 컨트롤러명);```
  - POST
    - ```라우터명.post("경로", 컨트롤러명);```
  - 한 페이지로 GET, POST 모두 할 때
    - ```라우터명.route("경로").get(컨트롤러명).post(컨트롤러명);```

## <br> MongoDB
- SQL이 아닌 문서 기반 데이터베이스이며 JSON방식으로 저장할 수 있다.
- MongoDB 홈페이지에서 알려주는 대로 설치할 수 있는데 Mac, Windows에서 각각 다른 방법으로 설치가 가능하다.
- Windows나 Mac의 terminal을 열어서 ```mongod``` 명령어를 쳐서 설치가 잘 되어있는지 확인할 수 있다.
- ```mongo``` 명령어를 치면 mongoDB shell과 연결을 해준다. 이렇게 되면 mongoDB 명령어를 사용할 수가 있다.
- ```exit``` 명령어로 연결을 종료할 수 있다.

## <br> mongoose
- node.js와 mongoDB를 이어주는 다리 역할을 한다.
- 개발자가 자바스크립트로 코드를 적으면 mongoose가 mongoDB에게 전달해준다.
- 명령창에 ```npm i mongoose``` 라고 쳐서 설치할 수 있다.
- mongoose를 이용해 find, findById 등과 같이 model로 CRUD 기능을 수행하는 다양한 함수를 사용할 수 있다.

## <br> DB와의 연결
- mongoDB, mongoose를 모두 설차한 뒤 DB와 연결을 한다.
- 명령창에서 ```mongo``` 명령어를 쳤을 때 ```connecting to: ``` 다음으로 나오는 url이 바로 자신의 database에서 실행되고 있는 url인 것이다. 이 url을 복사하고 js파일을 새로 만든 다음 아래와 같은 코드를 작성한다.
  ```javascript
  import mongoose from "mongoose";

  mongoose.connect("mongodb://127.0.0.1:27017/원하는이름", {
      useNewUrlParser: true,
      useUnifiedTopology: true
  });

  const db = mongoose.connection;

  const funOpen = () => console.log("DB Connected");
  const funError = (err) => console.log("DB Error", err);

  db.on("error", funError);
  db.once("open", funOpen);
  ```
- 위의 js파일을 다 작성하면 서버관련 js파일에 ```import ./파일명``` 코드를 맨 위에 작성해준다.

## <br> Model
- DB 모델을 만들기 위해 우선 새로운 JS 파일을 생성한다.
- ```import mongoose from "mongoose"``` 코드를 작성한다.
- ```const 스키마변수명 = new mongoose.Schema({속성명: 자료형})``` 형태로 스키마를 정의한다.
- ```const 모델변수명 = mongoose.model("모델명", 스키마변수명);``` 형태의 코드를 작성 뒤 ```export default 모델변수명``` 코드를 작성한다.
- export한 모델을 DB연결 파일을 import한 곳 아래에 import 한다. 
- 참고로 DB연결파일, 모델관련파일 등 다양한 파일들을 서버관련 파일에 import하다 보면 서버파일 양이 너무 거대해지고 복잡해질 수 있다. 따라서 특징별로 코드를 나눠 다른 파일에다가 관리하는 것이 좋으므로 DB, model 등을 import하는 내용들을 JS파일을 새로 만들어 거기에다가 옮겨주는 것도 좋은 방법이다.

## <br> Async, Await
- async이 붙은 함수(asynchronous인 함수)에서 await가 붙은 코드는 동작이 정상적으로 완료될 때까지 기다려준다.
- 특히 DB에 데이터를 저장하는 컨트롤러인 경우에는 DB에 데이터가 저장하는데 시간이 걸리기 때문에 try-catch와 함께 이를 사용해주는 것이 좋다.

## <br> DB에 저장하기
- 컨트롤러에서 데이터를 DB에 저장하는데에는 save와 create 두 가지 방식이 있다.
- 우선 컨트롤러에 async을 붙인다.
- save방식
  ```javascript
  const 변수명 = new 임포트한모델명({
    //속성명: 값
  });
  await 변수명.save();
  ```
- create방식
  ```javascript
  await 변수명.create({
    //속성명: 값
  });
- save, create 모두 같은 기능을 하는데 create가 좀 더 간단하다.
- 에러 처리를 위해 try-catch와 함께 사용할 수도 있다.
  ```javascript
  try {
    await 변수명.create({
        //속성명: 값
    });
  } catch(error) {
    //에러처리 코드
  }

## <br> Mongoose의 미들웨어
- express에서 미들웨어가 request를 중간에서 가로채서 무언가를 한 다음 이어서 진행하는 것처럴 mongoose에서도 document에 무슨 일이 생기기 전이나 후에 미들웨어를 적용할 수 있다. 즉, 모델이 CRUD 기능을 수행하기 전,후에 미들웨어나 함수를 적용하는 것이다.
또한 express의 미들웨어 같이 중간에 무언가를 할 뿐 흐름을 방해하지는 않는다.
- 사용방법

  모델을 만든 파일 안에서 스키마를 생성한 다음 모델을 생성하기 전의 위치에 아래와 같은 코드를 작성한다.
  ```javascript
  스키마명.pre("save", async function () {
    //처리하고 싶은 코드
  })
  ```
  위처럼 코드를 작성하면 여러 hook 중에서 save를 수행하기 전에 코드 작성자가 작성한 pre 안의 함수를 수행하게 된다.
  
## <br> Static
- 생성한 모델을 이용해서 create, findById, findByIdAndUpdate 등의 기능을 수행할 수 있다. 하지만 이들은 모두 호출하는 hook가 제각각이라서 위에서 설명한 미들웨어의 pre 등의 기능으로는 한계가 있을 수 있다. 따라서 사용하는 것이 static이다. static은 create, findById 같이 모델을 통해 수행하는 함수를 개발자가 직접 만들어 주는 것이다.

- static 만드는 방법
  
  모델을 만든 파일에서 아래와 같은 코드를 스키마를 생성한 코드 아래에 작성한다.
  ```javascript
  스키마명.static("원하는이름", function(필요한 매개변수) {
    //처리하고 싶은 내용
  });
  ```
  생성한 static을 이용할 때에는 create를 이용할 때와 같이 ```import한 모델명.만든static명``` 를 작성하여 이용하면 된다.

## <br> 해시
- 회원가입을 할 때 다양한 정보를 저장하게 되는데 그 중 비밀번호같이 다른 사람에게 노출되지 말아야 하는 데이터 같은 경우에는 다른 데이터처럼 저장하면 안된다. 암호화를 시킨 다음 다른 사람에게 노출 되더라도 해석하지 못하게 해야 한다. 그렇게 하기 위해 해시를 사용한다.
- 사용방법
  1. 해시를 사용하려면 bcrypt를 설치해야 한다. ```npm i bcrypt``` 명령어를 명령창에 쳐서 설치한다.
  2. 모델을 생성하는 파일에서 설치한 bcrypt를 import한 다음 스키마를 만들고 모델을 생성하기 전에 pre를 이용해서 해시화 한다.
      ```javascript
      스키마변수명.pre('save', async function() {
        this.속성명 = await bcrypt.hash(this.속성명, 5);
      });
      ```
      여기서 hash의 인자로 들어가는 숫자 5는 해시를 수행하는 횟수를 의미한다.

## <br> 상태코드
- 2로 시작하는 상태코드 : 성공을 의미
  - 200 : 브라우저에게 계정이 성공적으로 생성되었다고 알려준다.
- 4로 시작하는 상태코드 : 에러를 의미
  - 400 : 클라이언트에서 발생한 에러 때문에 요청을 처리하지 못할 때 쓰임
- 사용방법
  ```javascript
  return res.status(400).render("파일명");
  ```
  위와 같이 컨트롤러에서 render를 할 때 res(respond 객체)와 render 사이에서 status(상태코드)를 작성하면 되며 에러처리를 할 때 이런식으로 render를 해주는 것이 좋다. 왜냐하면 예를 들어 회원가입을 할 때 사용자가 이미 존재하는 아이디와 같은 아이디를 작성해서 회원가입에 실패를 했는데 에러가 발생할 때 사용하는 상태코드를 사용하지 않으면 브라우저는 회원가입이 실패했는지 모르고 아이디와 비밀번호를 저장하겠냐는 화면을 띄워주기 때문이다.

## <br> 세션&쿠키
- 회원가입 이후에 아이디와 비밀번호를 맞게 입력하면 로그인에 성공을 하게 된다. 그런데 사용자가 로그인한 상태를 유지하면서 사이트를 사용하기 위해서는 사용자에게 쿠키를 보내야 한다. 쿠키에 대해 알기 위해서는 우선 세션에 대한 이해가 필요하다. 세션은 백엔드와 브라우저 사이의 메모리, 기록 같은 것이다. 세션이 작동하려면 백엔드와 브라우저가 서로에 대한 정보를 가지고 있어야 한다. 왜냐하면 그냥 백엔드가 브라우저의 요청을 처리하고 랜더하게 되면 연결이 끊기기 때문이다. 따라서 백엔드가 누가 요청을 보내는지 알기 위해 보내는것이 쿠키이고 이를 통해 로그인 상태를 유지할 수가 있다.
- express에서는 ```npm i express-session```명령어를 통해 express-session이라는 미들웨어를 설치해서 세션을 처리할 수가 있다.
- 사용방법
  1. 서버파일에 express-session을 import한다.
  2. router을 use하는 코드 앞에다가 아래와 같은 코드를 작성한다.
      ```javascript
      app.use(
        session({
          secret: "Hi",
          resave: true,
          saveUninitialized: true
        })
      );
      ```
  3. 위의 단계까지 완료하면 세션을 사용할 수가 있는데 세션을 저장할 수가 없다. 세션을 저장하기 위해서는 ```npm i connect-mongo``` 명령어를 통해 connect-mongo를 설치해야 한다.
  4. 그 다음 2번 단계에서 작성한 코드에 mongostore에 관한 코드를 작성하여 아래와 같이 완성한다.
      ```javascript
      app.use(
        session({
          secret: "Hello!",
          resave: true,
          saveUninitialized: true,
          store: MongoStore.create({ mongoUrl: "mongodb주소" }) //세션을 MongoDB database에 저장할 수 있게 된다.
        })
      );
      ```
  5. resave와 saveUninitialized를 false로 바꿔주면 세션을 수정한 경우에만 세션을 DB에 저장하고 쿠키를 보내주게 된다.
      ```javascript
      app.use(
        session({
          secret: "Hello!",
          resave: false,
          saveUninitialized: false,
          store: MongoStore.create({ mongoUrl: "mongodb주소" })
        })
      );
      ```
  
  6. maxAge는 쿠키가 얼마나 오래 있을 수 있는지 알려주는 것으로 아래 코드와 같이 이용하면 된다.
      ```javascript
      app.use(
        session({
          secret: "Hello!",
          resave: false,
          saveUninitialized: false,
          cookie: {
            maxAge: 20000 //값은 1/1000초 단위로 쓰면 된다.
          },
          store: MongoStore.create({ mongoUrl: "mongodb주소" })
        })
      );
      ```
  
  7. 위의 코드에서 secret나 mongoUrl의 값 같은 경우에는 가려주는 것이 좋다. 따라서 .env 파일을 생성해서 거기에 secret이나 mongoUrl 같이 가려주고 싶은 부분을 변수를 만들어서 값을 집어넣어주면 된다.

  8. 세션을 없앨 때에는 ```req.session.destroy();```(req는 request 객체) 코드를 작성하면 된다.

## <br> locals
- 미들웨어에서 locals를 이용하면 모든 pug 파일에서 locals의 변수를 이용할 수가 있다.
- 사용방법
  ```javascript
  respond객체.locals.변수명 = 할당하고 싶은 값;
  ```
  위와 같이 하면 컨트롤러에서 render를 할 때 변수를 넘겨주지 않아도 pug파일에서 변수를 이용할 수 있게 된다. 변수를 이용할 때 ```locals.변수명``` 과 같이 쓸 필요 없고 그냥 ```변수명```만 적어주면 된다.

  
## <br> dotenv
- .env파일에 있는 변수들을 접근할 수 있게 해준다.
- ```npm i dotenv``` 명령어를 통해 설치한다.
- 사용방법 2가지
  - env파일의 변수를 사용하는 파일의 가장 위에 ```require('dotenv').config();``` 라는 코드를 작성한다.
  - 위의 방식대로 하면 파일마다 코드를 작성해줘야하는 번거로움이 있다. 따라서 좀 더 간편하게 사용하고 싶으면 앱을 시작하는 가장 앞부분에 ```import "dotenv/config";``` 라는 코드를 작성한다.
  - 위의 두가지 방법 중 한가지를 거치면 ```process.env.변수명``` 코드를 이용해 env파일의 변수를 이용할 수 있다.