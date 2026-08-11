# oop 클래스 작성 가이드

1. 클래스 정의 기본 구조

```python
class ClassName:
    def __init__(self, param1, param2):
        self.param1 = param1
        self.param2 = param2

    def method_name(self):
        pass
```

- **클래스명은 `UpperCamelCase`(단어마다 대문자) 사용**
- 메서드명, 변수명은 모두 **snake_case**(`소문자_소문자`) 사용

1.  인스턴스 변수의 언더스코어 규칙

| 선언 방식 | 의미 | 외부 접근 | 주용도 |
| --- | --- | --- | --- |
| `self.name` | public (공개) 변수 | ✅ 가능 | 누구나 접근 가능 |
| `self._name` | protected (보호됨) 변수 | ✅ 가능 (단, "건들지 말자"는 약속) | 상속관계 등에서 사용 |
| `self.__name` | private (사적) 변수 | ❌ 직접 접근 불가 (`_ClassName__name`으로만 가능) | 내부 전용 |
| `self.__name__` | 특별 변수 | ✅ 가능 | Python이 정의한 특별 기능 (**init**, **str** 등) |

1. 상속 시 규칙

```python
class Animal:
    def sound(self):
        return "..."

class Dog(Animal):
    def sound(self):
        return super().sound() + " + 멍멍"
```

- 부모 클래스 메서드를 오버라이드할 경우 반드시 같은 이름 유지
- 상속받은 메서드는 `super()`로 접근 가능
