># NodeJS 공부 정리
## <br>NodeJS란?
- 자바스크립트 런타임
- 브라우저 밖에서 돌아가는 자바스크립트

## npm
- 자바스크립트 언어를 위한 패키지 매니저
- NodeJS와 같이 쓰이고 NodeJS와 상호작용 할 수 있게 해줌
- NodeJS를 설치하면 같이 설치됨
- npm을 이용해 다른 사람들이 만든 패키지를 쓸 수 있음. npm install (패키지명) 또는 npm i (패키지명) 이라는 명령어로 원하는 패키지를 다운받을 수 있다.

## package.json
- NodeJS 프로젝트를 할 때 가장 먼저 만들어야하는 파일로 package.json이라는 이름으로 생성해야 한다.
- 직접 만들기 보다는 npm 명령어를 이용해서 만든다.
- 만들 때 명령어
  1. npm init
  2. package name, version, description, entry point, test command, git repository, keywords, author, license 확인 또는 작성 후 엔터
  3. package.json 생성됨
- 생성한 package.json 파일은 원하는대로 수정해도 된다.
- main은 프로젝트의 대표파일로 package를 배포했을 때 다른 사람이 main으로 되있는 파일을 사용하게 된다. 파일명이 index.js라 할 때 명령창에 node index.js 라고 치면 실행 시킬 수 있다. 그런데 main파일은 필수가 아니라 생략해도 된다.
- scripts는 또다른 방법으로 파일을 실행하게 해준다. "scripts": {"abc": "node index.js"}일 때 명령창에 npm run abc 라고 치면 index.js 파일을 실행할 수 있다. 물론 명령어는 프로젝트 폴더 안에서 쳐야 한다. 폴더 밖이나 package.json이 없는 폴더에서 명령어를 치면 실행할 수 없다.

## express
- 서버를 만드는데 필요한 패키지
- 명령창에 npm i express 또는 npm install express를 쳐서 express를 다운 받을 수 있다.
- 다운 받기 전에는 package.json 파일을 비롯해 열려있는 파일들을 저장한다.
- 다운을 받고 난 후
  - node_modules와 package-lock.json 파일이 생성된다.
  - node_modules에는 express 외에 다른 필요한 패키지들도 있다.
    - express안에도 package.json파일이 있고 이 안에는 scripts, contributers, dependencies 등이 있다. dependencies는 express가 작동되려면 필요한 패키지들이다.
    - npm install express를 실행하면 express를 다운 받으면서 express의 dependencies도 같이 다운 받는다. 즉 express를 설치하면서 express가 의존하는 패키지를 같이 설치하고 express가 의존하는 패키지들을 설치하면서 이들이 의존하는 패키지도 같이 설치하는 것이다. 이 모든 것들을 npm이 해준다.
  - 기존에 만들었던 package.json 파일에 dependencies로 express가 생긴다. 이 역시 npm이 해주는 것이다.
  - package-lock.json은 패키지들을 안전하게 관리해준다. 즉 다른 사람이 프로젝트를 받아 npm i 명령어를 쳤을 때 그 사람도 같은 버전의 모듈을 설치할 수 있게 된다.
- 참고로 package.json에서 express dependencies가 존재한다면 npm i만 쳐도 node_modules와 package-lock.json 파일이 설치되면서 node_modules안에는 express와 express가 의존하는 패키지들이 들어있도록 설치가 된다. 이것 역시 npm이 package.json파일에서 dependencies를 보고 그 안에 있는 모듈들을 알아서 설치하는 것이다.
- npm i 명령어만 치면 npm이 package.json파일의 dependencies를 보고 필요한 모듈들을 알아서 설치해주므로 용량이 큰 node_modules는 깃허브에 올리지 않아도 된다. 깃허브에 안올리려면 .gitignore 파일을 만든 다음 /node_modules라고 치면 된다.