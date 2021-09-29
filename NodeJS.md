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