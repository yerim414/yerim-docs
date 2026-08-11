# mutable, immutable

[2.1.7 mutable vs immutable](https://wikidocs.net/32277)

**mutable : 가변성, 값을 변경할 수 있음**

**immutable : 불변성, 값을 변경할 수 없음**

| class | 설명 | 구분 |
| --- | --- | --- |
| list | mutable 한 순서가 있는 객체 집합 | mutable |
| set | mutable 한 순서가 없는 고유한 객체 집합 | mutable |
| dict | key와 value가 맵핑된 객체, 순서 없음 | mutable |
| bool | 참,거짓 | immutable |
| int | 정수 | immutable |
| float | 실수 | immutable |
| tuple | immutable 한 순서가 있는 객체 집합 | immutable |
| str | 문자열 | immutable |
| frozenset | immutable한 set | immutable |

불변적 객체는 메모리 안에 담겨 있는 값이 언제나 변하지 않는 객체를 의미한다.

가변적 객체는 메모리 안에 담겨 있는 값이 변할 수 있는 객체를 의미한다.

가변적 객체의 특성 **mutable** 예시

```python
a = [1, 2, 3]
b = a
b[0] = 100
print(a)  # [100, 2, 3]
```

list는 mutable 값이라 위 소스를 보면 a도 함께 바뀌고 있다.

불변 객체의 특성 **immutable** 예시

```python
a = (1, 2, 3)
a[0] = 10  # TypeError: 'tuple' object does not support item assignment
```

위 소스 처럼 요소를 수정하려고 하면 에러가 발생한다.

tuple은 대표적인 불변 객체 이다. 내부 값을 바꾸는 행위가 금지되어 있다.
