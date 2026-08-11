# TypeError: a bytes-like object is required, not 'str’

```python
TypeError: a bytes-like object is required, not 'str'
```

api로 토큰을 발급하고 작업하던중 위와같은 오류가 발생

이 에러는 byte 타입이 필요하나 str 타입을 사용하고 있어서 발생하던 오류였다.

응답값을 찍어보니

```python
b'{"access_token":"e..."}'
```

앞에 b 가 붙어있는 형태는 **바이트 문자열(bytes)"** 이라는 뜻이다. 파이썬에서는 문자열과 바이트 분자가 정확히 구분된다.

바이트와 문자는 아래와같은 관계가 있다.

- **str –> 디코딩 –> bytes**
- **bytes –> 인코딩 –> str**

```python
import json

raw_response = b'{"access_token":"example_token"}'  # 바이트 응답
decoded = raw_response.decode("utf-8")              # 문자열(str)로 변환
parsed = json.loads(decoded)                        # 딕셔너리로 변환

print(parsed["access_token"])  # → "example_token"
```
