# 스킬 설치 및 사용법

## 1. Claude 실행 후 아래 명령어 입력

```
/plugin marketplace add JuliusBrussee/caveman
/plugin install caveman@caveman
```

<figure><img src="../../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

여느 스킬과 같이 마켓플레이스 등록 후 설치

***

## 2. 사용

<figure><img src="../../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

./caveman 명령어를 사용하여 이용하면 된다.

**설치 후 위 명령어가 뜨지 않아 재시작 하였다. 혹시 뜨지 않을 경우엔 재시작 필수!**

<figure><img src="../../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

일단 명령어만 호출해보았는데도 말이 상당히 짧아졌다.

해당 모드를 끄고 싶을땐 /caveman off 를 치면 된다.

***

## 3. 부가기능

소스코드 외에도 다양한 부가기능이 있다.

* /caveman-commit - 짧은 Commit 메세지를 생성한다. 참고로 직접 커밋을 하는게 아닌 커밋 메세지를 간결하게 만드는 스킬이다
* /caveman-review - 코드 리뷰 결과를 간결하게 하게 대답한다.

<figure><img src="../../../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

* /caveman-comprass - Markdown 파일을 압축한다. claude.md 등 caveman 스타일로 줄이는 용도이다.
* caveman-stats - 현재 claude code 세션의 실제 토큰 사용량과 Caveman 적용으로 예상되는 절감량을 보여준다.

***

Caveman 스킬도 utlra 옵션을제공하지만실제 작업의 결과를 어느정도 확인해야 하기 때문에 내 기준에는 lite가 적당한거 같다.
