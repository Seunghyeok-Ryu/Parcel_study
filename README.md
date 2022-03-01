# Parcel
# 정적 파일 연결
## ico converter
- image를 favicon.ico로 convert시킬 수 있음
- <a href="https://www.icoconverter.com/">ico converter</a>

## parcel plugin static files copy
- <a href="https://www.npmjs.com/package/parcel-plugin-static-files-copy">plugin static</a>
  - 설치방법
```
$ npm -D parcel-plugin-static-files-copy
```
- 이용방법
  - package.json 폴더에 code 작성
  - static folder의 내용을 npm run dev 시 dist 폴더로 이동 실행(정적 파일 연결 방법)
  ```
  "staticFiles" : {
    "staticPath" : "static"
  }
  ``` 
  - static 폴더 생성 후 실행을 원하는 파일들 넣기

  # autoprefixer
  - 구 버전의 인터넷에서도 작동할 수 있게 해줌
  - npm 설치 후 package.json 에서 확인
  ```
  $ npm i postcss -D
  $ npm i autoprefixer -D
  ```
  - 이용방법
    - package.json에 code 작성
    - 옵션 작성
    ```
    "browerslist" : [
    "> 1%",
    "last 2 versions"
    ]
    ```
    - .postcssrc.js 폴더 생성
      - postcssrc.js 는 nodejs(CommonJS 방식) 환경에서 적용됨(일반 js는 ESM방식)
      - import(ESM) -> require(CommonJs), export(ESM) -> module.exports(CommonJs)
      - 
      ```js
      module.exports = {
        plugins : [
        require('autoprefixer')
        ]
      }
      ```
      - autoprefixer와 postcss의 version이 차이가나서 error발생 경우 생김. version을 낮춰줌
      ```
      $ npm i -D autoprefixer@9 
      ```
# babel
- ECMAscript(ES) 2015+ 이전의 버전과 호환 시켜주는 기능
- npm 설치
```
$ npm i -D @babel/core 
$ npm i -D @babel/preset-env
```
- 이용방법
  - package.json에 옵션 작성
   ```
    "browerslist" : [
    "> 1%",
    "last 2 versions"
    ]
    ```
  - .babelrc.js 폴더 생성
    - code 작성
    ```js
    module.exports = {
     presets : ['@babel/preset-env'],
       plugins: [
        ['@babel/plugin-transform-runtime'] // npm 설치 후 main.js에서 async,await 사용 시 호출
      ]
    }
    ```
  - main.js에서 code작성 후 확인
    - js에서 async 함수 await 사용 시 npm 설치 해야함
    ```
    $ npm i -D @babel/plugin-transform-runtiom
    ```
    ```js
    async function test() {
      const promise = Promise.resolve(123)
      console.log(await promise)
    }
    test()
    ```

# CLI(커맨드 라인 인터페이스)
- <a href="https://ko.parceljs.org/cli.html">Parcel</a>
