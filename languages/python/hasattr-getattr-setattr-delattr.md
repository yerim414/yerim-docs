# hasattr, getattr, setattr, delattr

1. hasattr(object, name)
    
    해당 객체에 특정 속성이 존재하는지 검사
    
    존재하면 True, 없으면 False
    
    ```python
    class User:
        name = "Yerim"
    
    user = User()
    
    print(hasattr(user, 'name'))  # True
    print(hasattr(user, 'age'))   # False
    ```
    

1. getattr(object, name, default=None)
    
    속성 값을 가져온다.
    
    속성이 없으면 예외발생, default 값을 지정하면 그 값을 대신 반환(dict에서의 get)
    
    ```python
    print(getattr(user, 'name'))             # "Yerim"
    print(getattr(user, 'age', '미정'))       # "미정"
    ```
    

1. setattr(object, name, value)
    
    객체에 속성 추가 또는 수정할 때 사용
    
    ```python
    setattr(user, 'age', 26)
    print(user.age)  # 26
    ```
    

1. delattr(object, name)
    
    속성 삭제
    
    ```python
    delattr(user, 'age')
    print(hasattr(user, 'age'))  # False
    ```
    

위 내장함수는 인스턴스 변수, 클래스 변수 구분 없이 접근할 수 있다.

```python
class Sample:
    class_var = "클래스 변수"
    
    def __init__(self):
        self.instance_var = "인스턴스 변수"

obj = Sample()

print(getattr(obj, 'class_var'))     # 클래스 변수"
print(getattr(obj, 'instance_var'))  # "인스턴스 변수"
```

setatrr 로 없던 변수도 추가가능하다. 단 인스턴스 변수로 추가된다.
