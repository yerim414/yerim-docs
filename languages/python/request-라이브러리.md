# request 라이브러리

`requests`는 **HTTP 요청을 보낼 때 사용하는 파이썬 라이브러리이다.**

requests는 내장 라이브러리가 아니므로 pip 로 설치

```bash
pip install requests
```

jsonplaceholder를 이용하여 requests module 연습

## GET

get은 데이터를 가져올때

```bash
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"
response = requests.get(url)

# 응답 데이터 출력
print(response.status_code)  # 200 (성공)
print(response.json())  # JSON 형태로 변환하여 출력
```

## POST

post는 신규 데이터를 insert 할때

```bash
import requests

url = "https://jsonplaceholder.typicode.com/posts"
data = {
    "title": "새로운 글",
    "body": "본문",
    "userId": 1
}

response = requests.post(url, json=data) #json 형태로 데이터를 전송

print(response.status_code)  # 201 (생성됨)
print(response.json())  # 응답 데이터 확인
```

## PUT

수정

```bash
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"
update_data = {
    "title": "수정된 제목",
    "body": "수정된 본문",
    "userId": 1
}

response = requests.put(url, json=update_data)

print(response.status_code)  # 200 (성공)
print(response.json())  # 응답 데이터 확인
```

## DELETE

삭제

```bash
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"
response = requests.delete(url)

print(response.status_code)  # 200 (성공)
print(response.text)  # 응답 확인
```
