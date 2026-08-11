# life span

[Lifespan Events - FastAPI](https://fastapi.tiangolo.com/advanced/events/)

FastApi의 Lifespan은 애플리케이션이 시작될 때와 종료될 때 실행할 로직을 정의하는 기능이다.

```python
from fastapi import FastAPI
from contextlib import asynccontextmanager

@asynccontextmanager
async def lifespan(app: FastAPI):
    # 앱 시작 시 실행할 코드
    print("앱 시작")
    
    yield
    # 앱 종료 시 실행할 코드
    print("앱 종료")

app = FastAPI(lifespan=lifespan)
```

구현은 간단하다 `@asynccontextmanager` 데코레이터를 이용하여 함수를 작성해주면된다.

yield를 기준으로 위가 start 시 실행되고, 아래는 shutdown의 역할이다.

```python
이 방법은 전체 애플리케이션에서 사용해야 하는 자원을 설정하거나 요청 간에 공유되는 자원을 설정하고, 또는 그 후에 정리하는 데 매우 유용할 수 있습니다. 예를 들어, 데이터베이스 연결 풀 또는 공유되는 머신러닝 모델을 로드하는 경우입니다.
```

현재 내부 작업중인 프로젝트에선 앱의 시작과 종료를 log에 남기는 용도로 사용중이다.
