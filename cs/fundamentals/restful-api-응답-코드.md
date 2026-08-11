# RESTful API 응답 코드

[[REST API] HTTP 응답 코드 간단 정리](https://devuna.tistory.com/78)

[REST API 관점에서 바라보는 HTTP 상태 코드(HTTP status code)](https://sanghaklee.tistory.com/61)

HTTP 응답 코드는 **3자리 숫자로 구성**되며, 첫 번째 숫자(100~500)에 따라 의미가 달라진다.

1. **2xx 번대(성공) 응답 코드**

| 상태 코드 | 의미 |
| --- | --- |
| **200 OK** | 요청 성공 (일반적인 성공 응답) |
| **201 Created** | 새 리소스가 성공적으로 생성됨 (POST 요청 성공 시 사용) |
| **202 Accepted** | 요청이 접수되었지만, 아직 처리되지 않음 (비동기 작업) |
| **204 No Content** | 요청 성공, 하지만 응답 본문이 없음 (DELETE 요청 후 사용) |

1. **4xx (클라이언트 오류) 응답 코드**

| 상태 코드 | 의미 |
| --- | --- |
| **400 Bad Request** | 잘못된 요청 (파라미터 오류, JSON 형식 오류 등) |
| **401 Unauthorized** | 인증되지 않음 (로그인이 필요함) |
| **403 Forbidden** | 접근 권한 없음 (권한 부족) |
| **404 Not Found** | 요청한 리소스를 찾을 수 없음 |
| **405 Method Not Allowed** | 허용되지 않은 HTTP 메서드 사용 (예: `DELETE /users` 허용되지 않음) |
| **409 Conflict** | 요청 충돌 (중복 데이터 등) |
| **429 Too Many Requests** | 요청이 너무 많음 (서버가 제한 설정함) |

1. **5xx (서버 오류) 응답 코드**

| 상태 코드 | 의미 |
| --- | --- |
| **500 Internal Server Error** | 서버 내부 오류 |
| **502 Bad Gateway** | 게이트웨이 또는 프록시 서버 오류 |
| **503 Service Unavailable** | 서버가 일시적으로 사용 불가능 |
| **504 Gateway Timeout** | 게이트웨이 요청 시간 초과 |
