# match-case

match는 python 3.10 버전부터 새로 도입된 제어 흐름 구조이다.

보자마자 switch 같다고 느꼈다.

if랑 차이점을 비교하면

| 구분 | `if` | `match` |
| --- | --- | --- |
| **용도** | 조건(비교, 논리식)에 따라 분기 | 값의 패턴(구조, 형태, 값)에 따라 분기 |
| **비교 기준** | 불리언(True/False) 조건 | 특정 값, 구조(튜플, 리스트, dict), 타입 등 |
| **유연성** | 다양한 조건, 복잡한 논리 가능 | 구조 기반으로 분기 처리에 최적 |
| **파이썬 버전** | 모든 버전에서 사용 가능 | Python 3.10 이상 |

단순 값 비교나 여러가지 복합한 조건이나 범위는 if 를 사용

데이터 구조, 타입에 따라 다르게 처리할땐 match를 사용하는게 낭르것닽다.

```python
def classify_number(n):
    match n:
        case int() if n < 0:
            return "음수 (int)"
        case int() if n == 0:
            return "0 (int)"
        case int():
            return "양수 (int)"
        case str():
            return "문자열 타입"
        case list():
            return "리스트 타입"
        case _:
            return "알 수 없는 타입"
```

match도 if 처럼 위에서부터 순차적으로 검사하고 처음 매칭된 케이스에서 멈추게 된다.

```python
def describe(data):
    match data:
        case int() as number if number > 0:
            return f"양의 정수 {number}"
        case int() as number if number < 0:
            return f"음의 정수 {number}"
        case list() as items if len(items) == 0:
            return "빈 리스트"
        case list() as items:
            return f"리스트 {items}"
        case str() as text if text.isnumeric():
            return f"숫자 문자열 {text}"
        case str() as text:
            return f"일반 문자열 '{text}'"
        case _:
            return "알 수 없는 타입"
```

match 문에서의 as는 패턴에 매칭된 값을 변수에 할당하는 역할을 한다.

첫번째 case에선 먼저 데이터가 int 타입인지 확인하고 매칭 된다면 그 값을 number에 할당한다. 

그리고 if 문으로 조건을 추가하여 검사한다.

만약 저게 if문이라면..

```python
if isinstance(data, int) and data > 0:
```

match-case가 조금 간단한거 같기도하다
