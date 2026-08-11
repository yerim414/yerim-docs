# API와 Endpoint

[API Endpoint는 무엇인가요?](https://loadfocus.com/ko-kr/glossary/what-is-an-api-endpoint)

## API (Application Programming Interface)

어떻게 사용할 것인지 정해놓은 규칙/설명서

시스템 간의 통신 방법을 정의한 인터페이스 이다.

클라이언트가 서버와 소통하기 위한 설명

```python
[회원 정보 API]
요청 URL: /users/{id}
요청 방식: GET
설명: 특정 id의 사용자 정보를 조회한다.
```

이런 설명 자체가 하나의 API이다.

API안에는 여러개의 endpoing가 존재할 수 있다.

## Endpoint

API에서 실제로 접근하는 URL 경로

특정 자원에 접근하기 위한 URL이다.

```python
GET /users/1
```

seq가 1인 사용자의 정보 를 가져오는 Endpoint 이다..

```python
API: 회원 관련 API
  - 설명: 사용자의 정보를 CRUD 할 수 있는 API
  - 포함하는 Endpoint:
    - GET /users          → 모든 사용자 목록 조회
    - GET /users/{id}     → 특정 사용자 조회
    - POST /users         → 사용자 생성
    - PUT /users/{id}     → 사용자 정보 수정
    - DELETE /users/{id}  → 사용자 삭제
```

하나의 API는 여러개의 Endpoint를 가질 수 있다.

- **API**: 기능 집합과 그 규칙 (설명서)
- **Endpoint**: 그 기능을 실제로 실행하는 접속 지점 (URL)
