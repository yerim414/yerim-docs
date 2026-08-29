# 스킬 설치 및 사용법

1. 설치

```
npx skills add https://github.com/vercel-labs/skills --skill find-skills --agent claude-code
```

find-skill는 플러그인이 아니다.

하나의 skill을 여러 Agent에서 사용할 수 있게 만들었기 때문에 npx skills 라는 cli를 제공한다

<figure><img src="../../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

전역으로 설치해주었다.

2. 사용법

사용법은 간단하다 설치가 완료되었으면 claude를 다시 실행하고 skill을 찾아달라고 하면 된다.

<figure><img src="../../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

문제 내용, 출제 형식에 쓸만한 스킬을 추천해줬다.

퀴즈 생성 스킬도 따로 있나보다, 역시나 installs 의 수 만큼 추천하는게 다르다.

ctf-skill이 무엇인가 한번 찾아보았는데

{% embed url="https://github.com/ljagiello/ctf-skills" %}

Agent가 CTF 문제를 분석하고 분야별 공갹 기법을 적용하도록 만든 대규모 skill 모음이다.



find-skills를 통해 여러 스킬을 이용해봐야겠다.
