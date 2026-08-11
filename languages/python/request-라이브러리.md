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

## verify 옵션 (SSL 인증서 검증)

requests 요청을 보낼때 `verify=false` 로 설정하여 요청할때가 있다.

**SSL 인증서 검증(Verification)을 활성화할지 비활성화할지 결정하는 옵션이다.**

HTTPS 요청을 보낼 때, requests는 자동으로 SSL 인증서(보안 인증서)를 검증한다.

`https://`로 시작하는 사이트에 요청을 보낼 때 그 사이트가 신뢰할 수 있는 사이트인지 확인하는 과정이 포함된다.

일부 자체 서명된 인증서(self-signed certificate)를 사용하는 사이트나, **신뢰할 수 없는 SSL 인증서**를 가진 서버에 요청을 보낼 때, SSL 인증서 검증이 실패할 수 있다. 그런 경우에 `verify=false`를 설정하면 **SSL 검증을 건너뛸 수 있다.**

만약 신뢰할 수 있는 인증서를 직접 지정하고 싶다면, SSL 인증서를 .pem 파일로 다운로드하여 verify 옵션에 지정할 수도 있다.

```bash
import requests

url = "https://example.com"
cert_path = "/path/to/certificate.pem"  # 인증서 파일 경로

response = requests.get(url, verify=cert_path) #verify True

print(response.status_code)
```

## allow_redirects 옵션 (리디렉션 방지)

request 요청을 보내는데 원하는 결과는 안나오고 로그인 페이지 결과를 받고 있었다.

api 요청 시 인증정보 때문에 로그인 페이지로 리디렉트가 되는것 같았다.

정확한 확인을 위해 requests 요청을 보낼때 `allow_redirects` 옵션을 이용하여 리디렉트 확인을 해보았다.

```python
response = requests.get(api_url, allow_redirects=False)
```

요청을 보낼때 기본적으로 allow_redirects 옵션은 True 이다.

`allow_redirects=False`로 설정하면 리디렉트를 따라가지 않고, **리디렉트 응답(3xx 상태 코드)을 그대로 반환한다.**

확인해보니 응답 코드 302 였고 api key가 누락되고 있었다 ㅜㅜ

```python
import requests

url = "http://example.com"

response = requests.get(url, allow_redirects=False)

if response.status_code in [301, 302]:
    new_url = response.headers["Location"]
    print(f"리디렉트 감지! 새 URL: {new_url}")
    response = requests.get(new_url)  # 직접 재요청
```
