## environment setting

**✔ dotenv**
env파일 구성을 javascript 내에서 쓸 수 있도록 해준다.
```
yarn add dotenv
```

env를 설정할 수 있도록 해주는 package 설치 후, [(dotenv package)](https://trend21c.tistory.com/2142) 

```txt
npm install dotenv-cli --save-dev
```
package.json 파일의 script 부분에 start:prod 를 다음과 같은 형식으로 만들어 준다.  

```txt
 "scripts": {
    "start": "react-scripts start",
    "start:prod": "dotenv -e .env.production react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
  }
```
yarn start 할 경우 개발 환경 변수 설정한 URL이 나오고 (.env.development)  
yarn start:prod 하는 경우 운영 환경 변수 설정한 URL이 나올 것이다. (.env.production)




   




