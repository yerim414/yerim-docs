# `__del__` vs `__exit__`

`__del__` 를 이용하여 자원 해제 처리를 하고 있는데 `__del__` 이 아닌 `__exit__`을 사용을 고려해보라는 리뷰 의견을 받았다.

[PEP 343 – The “with” Statement | peps.python.org](https://peps.python.org/pep-0343/#context-managers-in-the-standard-library)

`__exit__` 과 `__enter__` 는 Context Manager로 with 문을 사용할 수 잇게 해주는 객체이다.

with 문과 사용중이라면 파일 open을 하는것도 Context Manager

__exit__ 메소드는 with 블록이 끝나는 순간 자동으로 호출되는 메소드이다.

이 블록이 정상적으로 종료되던 예외가 발생하든 무조건 호출이 된다.

```python
class MyManager:
    def __enter__(self):
        print("자원 시작")
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        print("자원 정리")

with MyManager():
    print("작업 중")

# 출력 결과    
자원 시작
작업 중
자원 정리
```

그러면 왜 __exit__ 을 사용하라 하신걸까

`__exit__` 은 with 구문에서 빠져나오기 직전에 호출된다.

그러나 __del__ 은 호출 보장이 없다. `__del__` 메소드는 가비지 컬렉션에 의해 삭제될 떄 호출되지만, **호출시점이 보장되지 않는다.**

`__del__()`은 예측할 수 없기 때문에 **자원 정리용으로는 부적절하다.**

[[py] __del__에서 리소스 해제를 하면 안 되는 이유](https://jiniya.net/2024/12/python_raii/?utm_campaign=asb&utm_medium=blog&utm_source=awesome-blogs.petabytes.org)

정확한 종료 시점이 있는 __exit__ 으로 자원을 해제 하여야 안전할것같다.

db close나 api 로그아웃 처리등.. 바꿔야 할것같다. ㅜㅜ
