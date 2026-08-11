# express 서버 구성

## 익스프레스 프로젝트 생성

```jsx
npm install express-generator -g
```

제너레이터를 이용해 손쉽게 설정 install 해주기

![Untitled](../../.gitbook/assets/languages-nodejs-express-서버-구성-1.png)

```jsx
express --no-view server
```

server폴더 생성

view옵션 ejs와 pug가 있음

**server로 쓸꺼니 no view 설정**

![Untitled](../../.gitbook/assets/languages-nodejs-express-서버-구성-2.png)

생성한 파일로 이동하기 (cd server)

모듈 설치 (npm install)

![Untitled](../../.gitbook/assets/languages-nodejs-express-서버-구성-3.png)

npm start로 실행

3000번포트로 이동하여 확인하기

[http://본인아이피:3000/](http://192.168.210.122:3000/)

![Untitled](../../.gitbook/assets/languages-nodejs-express-서버-구성-4.png)

정상적으로 접속되는지 확인

![Untitled](../../.gitbook/assets/languages-nodejs-express-서버-구성-5.png)

구조 확인
