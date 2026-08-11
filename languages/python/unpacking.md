# Unpacking

파이썬의 언패킹은 리스트, 튜플, 딕셔너리와 같은 여러 값을 가진 객체를 풀어서 개별 변수에 할당하거나, 함수 호출 시 인자로 전달하는 기능

```python
numbers = (1, 2, 3)
a, b, c = numbers
print(a, b, c) # 1 2 3
```

numbers 튜플을 변수 a, b, c에 하나씩 풀어서 할당한다.

튜플 언패킹, 시퀀스 언패킹 이라고 한다.

```python
data = [10, 20, 30]

a, b, c = data
print(a, b, c)
```

리스트도 동일하게 언패킹 가능하다.

물론 왼쪽변수 갯수와 오른쪽 시퀀스 요소의 갯수가 같아야 한다. 다르면 value error 발생

```python
n, m = map(int, input().split())
```

코딩테스트에서 많이 사용하는 문장, 이것도 언패킹이다.

```python
nums = [1, 2, 3, 4, 5]

a, b, *rest = nums
print(a, b, rest)  # 1 2 [3, 4, 5]

*a, b = nums
print(a, b)  # [1, 2, 3, 4] 5

a, *b, c = nums
print(a, b, c)  # 1 [2, 3, 4] 5
```

위처럼 남은 값을 리스트로 받을 수 있다.

```python
a, b, c = [1, 2, 3]
d = a, b, c
print(d) # (1, 2, 3)
```

반대로 적게되면 튜플로 묶을 수 있다. 이러면 패킹 이라 생각하면 될려나
