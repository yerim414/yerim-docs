# JWT 토큰 프로젝트

## **Json Web Token**

JWT는 인증에 사용되는 토큰 기반 인증 방식 중 하나이다.

## JWT의 구조

```python
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9. # Header
eyJ1c2VyX2lkIjoxLCJuYW1lIjoiSm9obiBEb2UifQ. # payload
H8d1gVEwMHKpUkM0qkLgU2jWbWSTQ7VbmMQPwvZ1M3U # signatture
```

. 을 기준으로 3가지 영역으로 구성되어 있다

- Header : 토큰의 타입과 알고리즘(ex:sha256)
- Payload : 실제 데이터(ex: 사용자 정보, 만료시간 등..)
- Signature : 위 2개를 서버의 비밀 키로 서명한 값

## 사용 흐름

1. 사용자가 로그인 사용자 정보(아이디, 패스워드)를 서버에 전달
2. 서버는 인증이 성공하면 JWT 를 생성 후 클라이언트에 반환
3. 클라이언트는 반환받은 JWT를 저장
4. 이후 요청 시, 클라이언트는 **Authorization 헤더에 JWT를 포함**하여 요청
5. 서비는 JWT를 검증하여 사용자 정보 확인 및 처리

1 ~ 3 번까지가 로그인 이전, 즉 로그인 성공 시에 이루어 지는 process, 4번과 5번은 로그인 이후의 과정이다.

[파이썬으로 간단 JWT 사용](파이썬으로-간단-jwt-사용.md)

[JWT 인증 토큰 검사](jwt-인증-토큰-검사.md)
