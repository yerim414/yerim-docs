# I/O 바운드 vs CPU 바운드 작업에서 각각 어떤 방법을 써야 효과적인가

### I/O 바운드 (Input/Output Bound)

프로그램이 CPU 연산보다 입출력 작업(I/O) 대기 때문에 속도가 느려지는 경우

CPU는 할 일이 없는데 디스크, 네트워크, DB, 파일 읽기/쓰기 같은 I/O 작업이 끝날 때 까지 기다려야 해서 전체 성능이 떨어짐

- 파일 다운로드 / 업로드
- DB 쿼리 실행 후 결과 기다리기
- API 요청 (HTTP request)
- 대용량 로그 파일 읽기

**주로 대기시간이 문제인것들.**

### CPU 바운드(CPU Bound)

프로그램이 I/O 대기 없이 CPU 연산이 많아서 속도가 느려지는 경우

CPU가 끊임없이 계산해야 하기 때문에 병목이 발생

- 대규모 수학 계산 (행렬 연산, 소수 찾기, 암호화/복호화)
- 이미지/영상 처리
- 머신러닝 모델 학습
- 데이터 압축/해제

**주로 계산량이 문제인 것들**

---

### I/O 바운드 → 비동기, 멀티스레딩 권장

대기하는 동안 다른 작업을 처리하면 효율적이다.

비동기 async : 이벤트 루프로 여러 I/O를 동기에 기다리기

멀티스레딩 → 스레드 마다 I/O 대기, CPU는 다른 스레드 실행 가능

```python
import asyncio
import aiohttp

async def fetch(session, url):
    async with session.get(url) as resp:
        return await resp.text()

async def main():
    urls = ["https://example.com", "https://google.com"]
    async with aiohttp.ClientSession() as session:
        results = await asyncio.gather(*(fetch(session, u) for u in urls))
        print(results)

asyncio.run(main())
```

### CPU 바운드 → **멀티프로세싱 권장**

Python의 경우 **GIL(Global Interpreter Lock)** 때문에 한 번에 한 스레드만 CPU 연산을 수행한다.

CPU 연산이 많을 때는 프로세스를 여러 개 만들어 CPU 코어를 병렬로 활용하는게 효율적이다.

```python
from multiprocessing import Pool
import math

def heavy_task(n):
    return sum(math.sqrt(i) for i in range(n))

if __name__ == "__main__":
    with Pool(processes=4) as pool:  # CPU 코어 4개 사용
        results = pool.map(heavy_task, [10_00000, 20_00000, 30_00000, 40_00000])
        print(results)
```
