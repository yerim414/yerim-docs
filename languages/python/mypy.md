# mypy

[mypy - Optional Static Typing for Python](https://mypy-lang.org/)

[https://github.com/python/mypy](https://github.com/python/mypy)

이전 글에서 typing 작성하면서 말한 타입 검사기

mypy는 작성된 타입 힌트를 기반으로 코드를 분석하여 잘못된 타입 사용에 대해 알려준다.

파이썬 자체, 파이썬 인터프리터는 타입힌트를 무시하지만 mypy는 그 타입 힌트를 이용하여 오류를 미리 확인 가능

```python
pip install mypy
```

사용방법

```python
def greet(name: str) -> str:
    return f"Hello, {name}"
```

이름을 출력해주는 간단한 함수 작성 이름은 str타입을 받도록 되어있고 리턴형식도 str이다.

```python
mypy hello.py
```

실행 방법은 mypy 명령어 뒤 검사하고 싶은 파일을 적으면 된다.

```python
Success: no issues found in 1 source file
```

아직 문제는 없다 그러면 저 함수의 리턴값을 바꿔보면

```python
def greet(name: str) -> str:
    return 100
```

숫자를 리턴하게 바꾸었다. 그냥 python 실행하듯이 한다면 오류와 경고는 나지 않겠지만

```python
wrong.py:2: error: Incompatible return value type (got "int", expected "str")
```

mypy로 확인 시엔 오류가 발생한다.

**mypy는 타입만 검사한다. 실제 코드를 실행하거나 수장하지 않는다.**

근데 이 글을 작성하면서 보니까. pyright도 있던데 이건 vscode에 연동이 가능하다고 한다.
