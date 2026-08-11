# for-else

[2.5 for-else와 while-else](https://wikidocs.net/190098)

파이썬은 for랑 else랑 같이 쓸 수 있다고 한다.

파이썬에서만 있다고 한다.

```python
for 변수 in 반복가능한_객체:
    # 반복 처리
    if 조건:
        break
else:
    # break 없이 정상적으로 반복문이 끝났을 때 실행
```

else는 반복이 끝났을 때 실행하는데 위에서 break로 중단된 경우 실행하지 않음

뭔가 finally 같으면서도 안같다..

for-else를 언제 쓸까 생각해 보았는데 아래 소스를 보면 이해하기 쉽다.

```python
found = False
for item in items:
    if some_condition(item):
        found = True
        break

if not found:
    print("조건에 맞는 값이 없음")
```

일반적으론 보통으로 그동안 해왔던것으론.. 위 처럼 작성을 했다

```python
for item in items:
    if some_condition(item):
        break
else:
    print("조건에 맞는 값이 없음")
```

그런데 이렇게 깔끔하게 처리가 가능해진다.

지피티한테 예시 몇개 물어보니

```python
n = 17
for i in range(2, int(n**0.5) + 1):
    if n % i == 0:
        print(f"{n}은 소수가 아닙니다.")
        break
else:
    print(f"{n}은 소수입니다.")
```

이렇게도 가능

주의점은 else는 break가 없을 때만 실행된다는것이고

continue는 영항을 주지 않는다는것이다.
