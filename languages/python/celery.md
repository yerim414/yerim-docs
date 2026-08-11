# Celery

[celery: 분산 작업 큐 시스템](https://wikidocs.net/230419)

Celery는 백그라운드에서 작업(비동기 작업)을 처리해주는 작업 큐(Task Queue)이다.

오래걸리는 작업 대용량 데이터 처리, 외부 api 요청이나 예약작업등.. 백그라운드에서 진행하는 작업을 처리할때사용한다.

```python
웹서버(Fast API)
-> 작업 동기화 요청
-> 작업 큐( Redis )
-> celery Worker (작업 처리)
-> 결과 저장
```

```python
사용자 ──> FastAPI ──> Redis (Broker) ──> Celery Worker
                    ↑               ↓
                작업 요청       작업 처리
```

구성요소

- Broker : 작업 요청을 저장하는 큐 (Redis, RabbitMQ)
- Worker : 작업을 받아서 처리하는 Celery 엔진
- Task : 처리하고자 하는 데이터

```python
pip install celery
```

패키지 인스톨

그 다음 브로커로 쓸 redis는 도커 컨테이너로 올리거나 구축한 서버로 연결해주기

```python
# tasks.py
from celery import Celery

app = Celery('tasks', backend='redis://localhost:6379', broker='redis://localhost:6379')
 
@app.task
def add(x, y):
  return x + y
```

Celery 인스턴스의 첫번째 매개변수는 해당 모듈의 이름(파일명), 그 다음 백엔드는 작업 결과를 저장 할 서버, broker는 작업 요청을 저장하는 큐

@app.task : Celery가 처리할 수 있는 비동기 작업

```python
celery -A tasks worker --loglevel=info
```

위 명령어로 워커를 실행한다. 

tasks.py 파일에서 Celery 앱을 찾겠다는 뜻

```python
python
>>> from tasks import add
>>> result = add.delay(4, 6)
>>> result
<AsyncResult: SOME-ID>

>>> result.get()
10
```

지금 mongodb를 메세지 큐 처럼 사용하고 있는데 이런거도 있구나 하고 찾아본 celery
