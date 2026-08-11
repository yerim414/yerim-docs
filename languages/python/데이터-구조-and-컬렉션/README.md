# 데이터 구조 & 컬렉션

## **1. 리스트 (list)**

- 순서(인덱스)가 있는 **배열 형태의 자료구조**
- **중복 허용**
- 값 **변경 가능**

```bash
# 리스트 생성
my_list = [1, 2, 3, 4, 5]

# 요소 접근 (인덱스 사용)
print(my_list[0])  # 1
print(my_list[-1])  # 5 (뒤에서 첫 번째)

# 리스트 수정 (변경 가능)
my_list[1] = 99
print(my_list)  # [1, 99, 3, 4, 5]

# 리스트 길이 확인
print(len(my_list))  # 5
```

## 2. 튜플 (tuple)

- 리스트와 비슷하지만 **값 변경 불가 (Immutable)**
- **빠른 속도**와 **메모리 절약**이 필요할 때 사용

```bash
my_tuple = (1, 2, 3, 4, 5)

# 요소 접근
print(my_tuple[0])  # 1
print(my_tuple[-1])  # 5

# 요소 변경 (불가능)
# my_tuple[0] = 10  # 오류 발생
```

## 3. 딕셔너리 (dict)

- **Key-Value(키-값) 구조**로 데이터 저장
- **순서 유지** (Python 3.7 부터)
- 키는 **유일해야 하며**, 변경 불가능한 값(str, int, tuple 등)만 가능

```bash
# 딕셔너리 생성
person = {"name": "Alice", "age": 25, "city": "Seoul"}

# 키를 이용한 값 접근
print(person["name"])  # Alice
print(person.get("age"))  # 25 (get 사용 시, 키가 없어도 오류 발생 X)

# 값 변경 & 추가
person["age"] = 26  # 값 변경
person["job"] = "Engineer"  # 새 키-값 추가
print(person)

# 키 삭제
del person["city"]
print(person)
```
