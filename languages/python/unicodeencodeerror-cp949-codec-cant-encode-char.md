# UnicodeEncodeError: 'cp949' codec can't encode character '\U0001f680' in position 123: illegal multibyte sequence

로깅에 이모티콘을 추가하였는데

```python
UnicodeEncodeError: 'cp949' codec can't encode character '\U0001f680' in position 123: illegal multibyte sequence
```

이런 오류 발생

이 오류는 **로깅 메시지에 포함된 이모지(🚀)가 Windows의 기본 콘솔 인코딩(cp949)에서 지원되지 않아서 발생하는 문제**입니다. 즉, 로그를 출력할 때 `stream.write(msg + self.terminator)` 과정에서 이모지 문자를 cp949로 인코딩하려고 했는데, 해당 문자가 cp949에서 지원되지 않기 때문에 `UnicodeEncodeError`가 발생한 것입니다.

라고 지피티가 알려줬다. …

나만 윈도우를 써서 다들 이런 오류가 안난다 했는데 ㅜㅜ

```python
file_handler = logging.FileHandler("log.txt", encoding="utf-8")
```

로그쪽에 `encoding = “utf-8”` 만 추가 해 주었더니 해결..
