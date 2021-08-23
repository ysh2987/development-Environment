# bundler
- bundler란 웹 개발자가 하위 툴 그룹을 관리하는데 도움을 주는 도구이다.
- react, vue, scss등 새로운 언어를 웹 브라우저가 읽을 수 있는 html, css, javascript로 자동으로 변환 시켜준다.
- ES6이상 문법들이나 flex, grid와 같은 css 새로운 기술들도 오래된 브라우저에서도 해당 문법을 읽을 수 있도록 해줍니다.
- bundler에는 parcel, webpack, Rollup 등이 있다.
## parcel
- 구성 없는 단순하고 빠른 자동 번들링
    - 소/중형 프로젝트에 적합
    - https://ko.parceljs.org/

## webpack 
- 매우 꼼꼼한 구성
    - 중/대형 프로젝트에 적합 
    - https://webpack.js.org/
---- 
## parcel-bundler 사용 환경
- npm이 설치되있어야 한다.
- npm init -y 
- npm i -D parcel-bundler 
- package.json / scripts 부분을
    - "dev": "parcel index.html",
    - "build" : "parcel build index.html"로 변경 


## 정적 파일 연결
  - 기본으로 작성한 html, scss. js등이 build 과정을 거쳐 dist폴더에 변환된 소스코드로 나타난다.
  - 그렇기 떄문에 favicon.ico같은 파일은 직접 dist 폴더에 넣어줘야한다

- npm i -D parcel-plugin-static-files-copy 설치
```
// package.json 파일에
"staticFiles": {
    "staticPath": "static"
  } 설정
```
static 폴더안에 favicon을 넣어주면 복사해서 dist 폴더로 옮겨준다.

- 최신 css 속성을 자동으로 구 브라우저에서도 동작하도록 하는 방법
- npm i -D postcss
- npm i -D autoprefixer
```
// package.json 파일에
  "browserslist": [
    "> 1%",  // 사용률이 전세계에서 1% 이상
    "last 2 versions" // 마지막 2개 버전까지  
  ]
```
.postcssrc.js 파일 생성
```
// node환결 이기때문에 module.exports사용
module.exports = {
    Plugins: [
        require('autoprefixer')
    ]
} 
```

- babel
  - ES6이상 코드를 이전  JS엔진에서 실핼 할수 있는 이전 버전과 호환되는 JS버전으로 변환

## 부가적인 속성들은 https://ko.parceljs.org/ 에서 확인해 사용한다

