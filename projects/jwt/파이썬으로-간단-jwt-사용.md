# 파이썬으로 간단 JWT 사용

파이썬에서 간단하게 JWT 사용 소스 작성

1. 라이브러리

```python
pip install PyJWT
```

인스톨 하기전엔 꼭 가상화를 해주기..

```python
import jwt
```

임포트는 jwt로!

1. 코드 작성

```python
import jwt
import datetime

SECRET_KEY = "mysecretkey"

# 토큰 생성
payload = {
    "id": "yerim",
    "mail" : "test@test.com"
    "exp": datetime.datetime.utcnow() + datetime.timedelta(minutes=30)
}

token = jwt.encode(payload, SECRET_KEY, algorithm="HS256")
print(f"Generated Token: {token}")

# 토큰 검증 및 디코딩
try:
    decoded = jwt.decode(token, SECRET_KEY, algorithms=["HS256"])
    print("Decoded Payload:", decoded)
except jwt.ExpiredSignatureError:
    print("Token has expired.")
except jwt.InvalidTokenError:
    print("Invalid token.")
```

간단하게 작성 하였다

1. 코드 설명

```python
import datetime
```

토큰의 만료 시간을 설정하기 위해 import

```python
SECRET_KEY = "mysecretkey"
```

시크릿 키는 jwt 를 서명하거나 검증할때 사용하는 비밀 키 이다.

외부에 절대로 노출되면 안된다!! 일단은 임시로 작성한 소스코드이니 하드코딩한다.

이 키를 이용하여 encode, decode를 수행하니 잃어버려서도 안된다.

```python
# 토큰 생성
payload = {
    "id": "yerim",
    "mail" : "test@test.com"
    "exp": datetime.datetime.utcnow() + datetime.timedelta(minutes=30)
}

token = jwt.encode(payload, SECRET_KEY, algorithm="HS256")
print(f"Generated Token: {token}")
```

토큰 생성을 위해 payload 데이터를 정의 한다. 

payload는 jwt에 담길 데이터 이다. 토큰의 내용물 이라고 생각하면 된다.

exp는 토큰의 만료 시간을 넣어뒀고 utc 기준으로 30분간 유효한 토큰이다

```python
token = jwt.encode(payload, SECRET_KEY, algorithm="HS256")
print(f"Generated Token: {token}")
```

데이터를 인코딩하여 jwt 문자열을 생성한다.

jwt 토큰을 암호화 할때 많이 쓰이는 HS256 알고리즘으로 인코딩을 한다

```python
Generated Token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxMjMsImV4cCI6MTc1MTE4NjY0Nn0.Erjzumazfxg6MbaV96xNrybgQLr1jx_gFjDHoh6f_q4
```

print를 하면 문자열 형태의 jwt가 생성 찍히게 된다.

```python
# 토큰 검증 및 디코딩
try:
    decoded = jwt.decode(token, SECRET_KEY, algorithms=["HS256"])
    print("Decoded Payload:", decoded)
except jwt.ExpiredSignatureError:
    print("Token has expired.")
except jwt.InvalidTokenError:
    print("Invalid token.")
```

decode를 하여 palyload 데이터를 꺼낼 수 있다. 이때 인코딩할때 사용하엿던 secret_key 가 필요하다.

지정한 exp 시간이 지나 토큰이 만료가 되면 Token has expired. 가 출력

시크릿 키가 잘못되었거나 토큰이 손상되면 Invalid token. 가 출력 된다.
