# list 에서의 in 사용 → set을 이용하자

[https://github.com/VSFe/Algorithm_Study/blob/main/Concept/Prev/vol.2/00_Special/Pythonic_Code_For_Coding_Test.md](https://github.com/VSFe/Algorithm_Study/blob/main/Concept/Prev/vol.2/00_Special/Pythonic_Code_For_Coding_Test.md)

코딩 테스트 공부를 하다가 보게된 글

초보자분들이 가장 많이 하는 실수가, **값을 찾기 위해 list에서 in을 사용한다는 것** 입니다.

왜 실수인지 하나씩 설명 하자면…

in 연산자의 동작 방식

```python
nums = [1, 2, 3, 4, 5]
print(3 in nums)   # True
print(10 in nums)  # False
```

in 연산자는 리스트 전체를 앞에서부터 끝까지 순차 탐색(linear search)을 한다.

리스트의 길이가 n 이라면 최악의 경우 시간복잡도는 O(n) 이 걸리는 셈

```python
list_ = [random.randint(0, 10**7) for _ in range(10**6)]

print(4 in list_)
```

위 코드에서 4 라는 값이 한번의 비교로 끝난다면(best case) 좋겠지만 최악의 경우 없거나 끝에 있으면.. 수십~수백 ms가 걸릴수 있다.

더 좋은 방법은 집합(set)을 사용하는 방법이다.

set은 내부적으로 해시 테이블 로 구현되어 있다.

- 요소를 추가할 때:
    1. 값을 해시 함수(`hash()`)에 넣어 → 특정 숫자(해시값)를 얻음
    2. 그 해시값을 이용해 메모리 상의 위치(버킷)에 저장
- 값을 검색할 때 (`x in set_`):
    1. 똑같이 `x`를 해싱
    2. 해당 해시값에 해당하는 메모리 슬롯만 확인

시간복잡도: **O(1)** (평균적으로 즉시 찾을 수 있음)

```python
set_ = {random.randint(0, 10**7) for _ in range(10**6)}  # 백만 개 (집합)
print(4 in set_)  # 해시 테이블 탐색 O(1)
```

참고로 set은 알다시피 중복값 허용이 되지 않는다!

리스트에서 set 으로 변경시엔 중복값이 자동으로 제거되니 알아두기
