# requests 요청 시 redirection 방지

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
