# requirements.txt

requirements.txt 파일은 **Python 프로젝트에서 필요한 패키지(라이브러리) 목록과 해당 버전 정보를 기록** 하는 파일입니다.

이 파일을 사용하면 같은 프로젝트를 다른 환경에서도 동일한 패키지와 버전으로 설치할 수 있습니다.

프로젝트마다 가상환경을 만들어줘서 독립적인 환경을 유지하는것이 좋습니다.

1. requirements.txt 생성

```bash
pip freeze > requirements.txt
```

설치된 패키지를 위의 명령어를 통해 requirements.txt로 만들 수 있습니다.

```bash
pip list --format=freeze > requirements.txt
```

--format=freeze 옵션을 추가하여 정확한 버전으로 requirements.txt를 만들자

1. 패키지 설치

```bash
pip install -r requirements.txt
```

위의 명령어를 이용하면 requirements.txt에 적힌 패키지들이 설치됩니다.

로컬에서 설치 시에도 가상환경을 만들어서 프로젝트별로 관리 하는것이 좋다. 충돌이 날 수 잇다..

다른 프로젝트의 requirements.txt 설치를 할려하면 가끔 지원 안하는 패키지가 있을 수 있다. 그럴땐 requirements.txt에서 오류나는 패키지에 주석 처리나 최대, 최소 버전으로 조정해 준다.

```bash
Django==4.1.5
requests>=2.26.0
numpy
pandas>=1.3.0,<1.5.0
```

- `==` : 정확한 버전 지정 (예: `Django==4.1.5`)
- `>=` : 최소 버전 지정 (예: `requests>=2.26.0`)
- `<` : 최대 버전 지정 (예: `pandas>=1.3.0,<1.5.0` → 1.3.0 이상, 1.5.0 미만 설치)
