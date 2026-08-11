# requests verify 변수

requests 요청을 보낼때 `verify=false`  로 설정하여 요청할때가 있다.

**SSL 인증서 검증(Verification)을 활성화할지 비활성화할지 결정하는 옵션이다.**

HTTPS 요청을 보낼 때, requests는 자동으로 SSL 인증서(보안 인증서)를 검증한다.

[https://로](https://xn--2o2b/) 시작하는 사이트에 요청을 보낼 때 그 사이트가 신뢰할 수 있는 사이트인지 확인하는 과정이 포함된다.

일부 자체 서명된 인증서(self-signed certificate)를 사용하는 사이트나, **신뢰할 수 없는 SSL 인증서**를 가진 서버에 요청을 보낼 때, SSL 인증서 검증이 실패할 수 있다. 그런 경우에  `verify=false`를 설정하면 **SSL 검증을 건너뛸 수 있다.**

만약 신뢰할 수 있는 인증서를 직접 지정하고 싶다면, SSL 인증서를 .pem 파일로 다운로드하여 verify 옵션에 지정할 수도 있다.

```bash
import requests

url = "https://example.com"
cert_path = "/path/to/certificate.pem"  # 인증서 파일 경로

response = requests.get(url, verify=cert_path) #verify True

print(response.status_code)
```
