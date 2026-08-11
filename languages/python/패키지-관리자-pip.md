# 패키지 관리자 pip

[51. pip - 패키지 매니저](https://wikidocs.net/16374)

```python
pip = "Pip install Package"
```

pip는 파이썬의 패키지 관리 도구이다.

버전 확인

```python
pip --version
```

패키지 설치

```python
pip install 패키지명
```

특정 버전 설치

```python
pip install requests==2.28.0
```

최신 버전으로 업그레이드

```python
pip install --upgrade requests
```

패키지 삭제

```python
pip uninstall 패키지명
```

설치된 목록 보기

```python
pip list
```

설치된 패키지를 requiremets.txt로 저장

```python
pip freeze > requirements.txt
```

requiremets 문서 참고..

pip install 하기전 가상환경인지 확인을 하자…………
