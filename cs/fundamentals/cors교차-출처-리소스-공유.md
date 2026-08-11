# CORS(교차 출처 리소스 공유)

## **Cross Origin Resource Sharing**

웹 브라우저가 다른 출처(도메인, 프로토콜, 포트)에서 요청을 보낼 때 보안상의 이유로 차단되는 문제를 해결하는 메커니즘

**출처가 다른 서버 간의 리소스 공유를 허용**

웹 브라우저는 기본적으로 동일한 출처 정책을 따른다. (SOP, Same-Origin Policy)

**출처가 다르면 요청을 차단.**

예시

[http://example.com](http://example.com/) → [http://example.com](http://example.com/) : 동일한 출처 이므로 요청이 가능

[http://example.com](http://example.com/) → [https://example.com](https://example.com/) : 프로토콜이 다름 요청이 차단됨

[http://example.com:3000](http://example.com:3000/) → [http://example.com:5000](http://example.com:3000/) : 포트가 다름 요청이 차단됨

위와 같이 프로토콜이나 포트가 다른경우가 있다. 프론트에서 api요청을 하면 다른 도메인이나 포트로 요청을 보내게 될것이다. 아니면 open api 등등.. 이러한 경우 **CORS**가 필요하다.

서버에서 CORS 설정을 통해 특정 출처를 허용하면, 브라우저가 차단하지 않는다.

서버 응답 헤더에서 `Access-Control-Allow-Origin`을 설정하면 해결

```bash
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET, POST, PUT, DELETE
Access-Control-Allow-Headers: Content-Type
```

## Node.js에서의 cors 설정

```bash
const express = require('express');
const cors = require('cors');
const app = express();

// 모든 도메인에서 요청 허용
app.use(cors());

// 특정 도메인만 허용
app.use(cors({ origin: "http://localhost:3000" }));

app.get("/data", (req, res) => {
  res.json({ message: "CORS 설정 완료!" });
});

app.listen(4000, () => console.log("서버 실행 중..."));
```
