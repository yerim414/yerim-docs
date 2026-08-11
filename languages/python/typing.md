# Typing

[typing — 형 힌트 지원 — Python 3.10.17 문서](https://docs.python.org/ko/3.10/library/typing.html)

typing은 정적 타입 힌트를 위한 표준 묘듈, 동적 타입 언어인 파이썬에서 코드의 안정성, 가독성, 자동 완성 지원, 디버깅 효율을 높이기 위해 등장. typescript가 생각난다

```python
def add(a, b):
    return a + b
```

파이썬은 동적 타입 언어라서,  위 함수만 보면 이게 숫자를 더하는것인지 문자열을 더하는것인지 타입의 의도가 명확하지 않다. 만약 협엽을 하게된다면… 

```python
def add(a: int, b: int) -> int:
    return a + b
    
age: int = 30
name: str = "Alice"
```

위 코드처럼 타입 힌트를 도입하여 어떤 타입의 값을 받을건지, 설정할건지 알 수 있다!

int나 str이 아니고 list, tuple ,dict 모두 가능하다

```python
from typing import List, Dict, Tuple, Set

names: List[str] = ["Alice", "Bob"]
user_info: Dict[str, int] = {"age": 30}
position: Tuple[int, int] = (100, 200)
flags: Set[str] = {"admin", "active"}
```

```python
from typing import Optional, Union

def get_user(id: int) -> Optional[str]:
    return "user" if id == 1 else None

def load(data: Union[str, bytes]) -> str:
    if isinstance(data, bytes):
        return data.decode()
    return data
```

union은 str이나 bytes를 받을 수 있다는 의미이다. 

```python
def load(data: str | bytes) -> str:
    if isinstance(data, bytes):
        return data.decode()
    return data
```

union은 | 연산자로 간단히 표현할 수 있다.

| 타입 이름 | 설명 |
| --- | --- |
| `List[X]` | X 타입 리스트 |
| `Dict[K, V]` | 키: K, 값: V 딕셔너리 |
| `Tuple[X, Y]` | 고정 길이 튜플 |
| `Set[X]` | 집합 |
| `Optional[X]` | X 또는 None |
| `Union[X, Y]` | X 또는 Y |
| `Any` | 아무 타입 |
| `Callable` | 함수 타입 |
| `Literal` | 고정된 리터럴 값 지정 |
| `TypedDict` | 딕셔너리 구조를 명시적으로 지정 |
| `Final` | 변경 불가능한 값 (상수처럼 사용) |
| `Protocol` | 구조적 서브타이핑 |

근데 저렇게 타입 힌트를 작성하여도 **파이썬 자체에서는 무시**한다.

따로 타입을 체크 하는 패키지를 설치 하여 타입 체크가 가능하다.

가독성 부분에선 좋고 프로젝트 규모가 크다면 필수일것같다. 근데 그럴거면 typescript를 사용하지 않을까
