# map 함수

map() 함수는 반복 가능한 객체에 특정 함수를 적용 한다.

```python
map(함수, 반복 가능한 객체)
```

그리고 코딩 테스트에서 아래와 같이 많이 쓰인다.

```python
data_list = list(map(int, input().split()))
```

사용자로 부터 입력받은 데이터를 숫자형으로 바꿔준다.

map을 사용하지 않으면 리스트에 인덱스로 직접 접근해서 int로 바꿔주거나 for문을 이용해서 바꿔주거나

그리고 map을 사용하고 거의 list() 로 감싸게 되는데 그 이유는

```python
def to_upper(s):
    return s.upper()

words = ["hello", "world", "python"]

uppercase_words = map(to_upper, words)

print(uppercase_words)
print(list(uppercase_words))
```

위 소스를 실행해보면 결과는 다음과 같다

```python
<map object at 0x0000026A6810F3A0>
['HELLO', 'WORLD', 'PYTHON']
```

그냥 map을 print 하면 이터레이터 이므로 확인이 불가능하다.
이터레이터 객체를 한 번에 확인하려면 **`list()`를 사용하여 리스트로 변환** 해야 한다.
물론 for문을 이용해서 하나씩 빼도 된다
