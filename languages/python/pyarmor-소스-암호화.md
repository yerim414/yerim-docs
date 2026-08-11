# pyarmor 소스 암호화

[https://github.com/dashingsoft/pyarmor](https://github.com/dashingsoft/pyarmor)

파이썬 소스코드의 외부유출을 방지하기위한 방법의 하나

**소스 코드 보호** 및 **배포 보안**을 강화하는 도구

pyarmor 설치

```python
pip install pyarmor
```

난독화 할 파일을 다음 명령어 실행

```python
pyarmor gen hello.py
```

완료되면 dist 폴더가 생성되고 폴더 내부에 동일한 이름을 가진 파일이 생성된다.

실행은 python 실행하듯이 실행해주면 된다.

```python
python dist/hello.py
```

그런데 간단한 파일은 실행이 되지만 파일 내부에 다른 폴더를 import 하는 소스가 있으면 해당 import를 읽어오지 못한다.

```python
Traceback (most recent call last):
  File "<frozen __main__>", line 3, in <module>
  File "<frozen xmlDown>", line 8, in <module> 
ModuleNotFoundError: No module named 'models'
```

찾아보니 여러개의 파일, 프로젝트 폴더를 한번에 암호화 하는게 있긴하다

```python
pyarmor obfuscate -r my_project/
```

-r 옵션만 넣으면 된다. 옵션을 사용하면 폴더 내의 모든 Python 파일을 암호화한다.

한 파일을 암호화 하면 그 파일이 import 하는 다른 파일도 동일하게 해줘야 하는건가

그리고 이렇게 해두면 실행속도가 동일하진 않을거같다.

완벽한 보안도 아닐거같음..
