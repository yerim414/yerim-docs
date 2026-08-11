# yield

Yield는 맥락에 따라 동사로 '생산하다', '항복하다', '넘겨주다', '양보하다' 혹은 명사로 '수확량, 총수익'을 의미합니다.

**[출처]** [Yield 뜻과 예시](https://blog.naver.com/engram_blog/223324913517)|**작성자** [Engramㅣ엔그램](https://blog.naver.com/engram_blog)

yield는 주로 제너레이터에 사용되며, 함수의 실행 흐름을 중단하고 값을 임시 반환할 수 있게 하는 키워드 이다.

먼저 제너레이터를 알기전 이터레이터는 아래 소스코드를 보면

```python
my_list = [1, 2, 3]
it = iter(my_list)
print(next(it))  # 1
```

iterator는 반복 가능한 객체, 즉 반복문을 이용해서 데이터를 순회하면서 처리하는것을 의미한다.

`next()`로 값을 하나씩 꺼낼 수 있다.

그럼 제너레이터는 이터레이터를 생성해주는 함수를 의미한다. 제너레이터는 모든 값을 메모리에 담고 있지 않고,  그때그때 값을 생성해서 반환하기 때문에 제너레이터를 사용할때는 한번에 한개의 값만을 순환할 수 있다.

**호출할 때마다 한 개의 값을 리턴한다**

```python
def count_up_to(limit):
    num = 0
    while num < limit:
        yield num
        num += 1

g = count_up_to(1000000)  # 이 시점에 100만 개 숫자를 메모리에 올리지 않음
```
