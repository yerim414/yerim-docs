# ThreadPoolExecutor

[concurrent.futures — 병렬 작업 실행하기](https://docs.python.org/ko/3/library/concurrent.futures.html#threadpoolexecutor)

```python
import concurrent.futures
import urllib.request

URLS = ['http://www.foxnews.com/',
        'http://www.cnn.com/',
        'http://europe.wsj.com/',
        'http://www.bbc.co.uk/',
        'http://nonexistent-subdomain.python.org/']

# 페이지 하나를 가져오고 URL 과 내용을 보고합니다
def load_url(url, timeout):
    with urllib.request.urlopen(url, timeout=timeout) as conn:
        return conn.read()

# with 문을 사용하여 스레드가 즉시 정리되도록 할 수 있습니다
with concurrent.futures.ThreadPoolExecutor(max_workers=5) as executor:
    # 로드 작업을 시작하고 각 퓨처의 해당 URL을 기록합니다
    future_to_url = {executor.submit(load_url, url, 60): url for url in URLS}
    for future in concurrent.futures.as_completed(future_to_url):
        url = future_to_url[future]
        try:
            data = future.result()
        except Exception as exc:
            print('%r generated an exception: %s' % (url, exc))
        else:
            print('%r page is %d bytes' % (url, len(data)))
```

`max_workers = 5` : 동시에 5개 까지 실행 가능한 스레드를 생성한다.

`executor.submit(func, arg)`: 병렬 작업 하나를 등록 한다.

`future.result()` : 각 작업의 반환값을 가져온다.

| 항목 | 내용 |
| --- | --- |
| 위치 | `concurrent.futures` 모듈에 포함 |
| 역할 | **스레드 풀(thread pool)**을 만들어 병렬 작업 수행 |
| 특징 | `for`, `map`, `submit`, `as_completed` 등으로 쉽게 사용 가능 |
| 사용 목적 | **IO-bound 작업**에 적합 (예: 포트 스캔, 웹 요청, 파일 다운로드 등) |
