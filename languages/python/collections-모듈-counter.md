# collections 모듈 > Counter

[파이썬 collections 모듈의 Counter 사용법](https://www.daleseo.com/python-collections-counter/)

코딩테스트 문제 풀다가 Counter로 문제 푼 사람을 보게댐

`Counter`는 `collections` 모듈에 포함된 클래스 중 하나이다.

리스트, 문자열 ,튜플 등 반복 가능한 객체에서 각 요소의 개수를 세어주는 특수한 딕셔너리 자료형이다.

```python
from collections import Counter
```

collection을 임포트하여 사용.

```python
from collections import Counter

fruits = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple']
counter = Counter(fruits)

print(counter)
# 출력: Counter({'apple': 3, 'banana': 2, 'orange': 1})
```

키-값 상처럼 동작하며, 각 요소가 key, 등장 횟수가 value 로 지정

```python
text = "hello world"
char_counter = Counter(text)

print(char_counter)
# 출력: Counter({'l': 3, 'o': 2, 'h': 1, 'e': 1, ' ': 1, 'w': 1, 'r': 1, 'd': 1})
```

문자열에서도 사용 가능하다.

문자열에서의 단어 빈도 이런거로 사용 하면 될것같다.

여러개의 값 비교에서도 사용해도 될듯

```python
counter = Counter(values)
freq = counter.values()
```

임의의 길이 list values 변수 or 문자열 을 받고 해당 값들의 빈도만을 values로 추출하면 된다.
