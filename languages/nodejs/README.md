# Node.js

[Index | Node.js v21.7.1 Documentation](https://nodejs.org/docs/latest/api/)

Node.js는 Chrome V8 JavaScript 엔진 위에서 동작하는 JavaScript 런타임 환경이다.

즉, Node.js는 웹 브라우저가 아닌 서버 측에서 JavaScript 코드를 실행할 수 있게 해준다.

## node.js의 특징

**비동기식 (Asynchronous)**

Node.js API는 비동기식이다. 이는 Node.js가 입출력 작업 등 시간이 걸리는 작업을 기다리지 않고 다음 작업을 수행할 수 있게 해준다. 이러한 비동기식 처리 방식을 통해 대규모의 요청을 효율적으로 처리할 수 있다.

**모듈 시스템 (Module System)**

Node.js는 모듈 시스템을 기본적으로 제공한다. 이를 통해 코드를 모듈화하고 필요한 모듈을 다른 파일에서 불러와 사용할 수 있다. 이는 코드의 재사용성을 높이고 유지 보수를 용이하게 한다.

**단일 언어 사용**

Node.js는 JavaScript를 사용하기 때문에 프론트엔드와 백엔드 개발 모두에 동일한 언어를 사용할 수 있다. 이는 개발자들이 전체 애플리케이션을 통일된 방식으로 개발하고 유지보수할 수 있도록 도와준다.

## node.js의 단점

**단일 스레드 모델의 한계**

Node.js는 싱글 스레드 모델을 사용하므로 CPU 집약적인 작업을 처리하는 데는 적합하지 않다. 하나의 CPU 코어만 사용하기 때문에 멀티 코어 시스템에서는 CPU 활용도가 낮을 수 있다.

**콜백 지옥 (Callback Hell)**

비동기식 프로그래밍 모델은 콜백 함수를 중첩하여 사용하게 되는데, 이는 코드의 가독성을 저하시키고 디버깅을 어렵게 만들 수 있다. 이러한 문제를 해결하기 위해 Promise나 async/await와 같은 비동기 처리 방식을 사용할 수 있지만, 이 또한 학습 곡선이 있다.

[**Node.js에서 mysql db 백업**](node-js에서-mysql-db-백업.md)

[**Axios로 api 통신하기**](axios로-api-통신하기.md)

[nodemon 설정](nodemon-설정.md)

[**express 서버 구성**](express-서버-구성.md)

[**Express에 Swagger 적용하기**](express에-swagger-적용하기.md)

[**MongoDB 연결**](mongodb-연결.md)

[Unexpected token , in JSON at position](unexpected-token-in-json-at-position.md)

[Node scheduler](node-scheduler.md)

[Reduce](reduce.md)

[Map](map.md)

[Filter](filter.md)
