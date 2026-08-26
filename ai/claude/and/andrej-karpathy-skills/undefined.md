# 스킬 설치 및 사용법

karpathy 스킬을 내 클로드에 적용하기

md로도 올려도 되지만 skill로 등록하여 다른 프로젝트에서도 사용할 수 있게 할 수 있다.

1. claude 실행 후 아래 명령어 입력

```
/plugin marketplace add forrestchang/andrej-karpathy-skills
```

<figure><img src="../../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

2. 플러그인 설치

```
/plugin install andrej-karpathy-skills@karpathy-skills
```

<figure><img src="../../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

설치시엔 scope를 고를 수 있다. 무조건 전역 설치가 아닌 어디까지 적용되는지 선택 할 수 있다

| 스코프         | 저장 위치                         | 적용 범위                         |
| ----------- | ----------------------------- | ----------------------------- |
| **User**    | `~/.claude/settings.json`     | 내 모든 프로젝트                     |
| **Project** | `.claude/settings.json`       | 이 저장소 — **git에 올라가 팀원에게도 적용** |
| **Local**   | `.claude/settings.local.json` | 이 저장소, **나만**                 |

일단 난 이 저장소에서 나만 쓸거기 때문에 Local 선택



3. 설치 확인

.claude/setting.json에 보면 설치한 스킬이 적용되어 있다.

만약 사용하지 않을 경우엔 true -> flase로 변경해주면 된다.

<figure><img src="../../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

4. 요청하여 확인해보기

일부러 애매한 요청을 던져서 잘 되는지 확인해보기

<figure><img src="../../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

그렇게.. 큰 기능이 없는 프로젝트라 그런지 성공적으로 스킬은 로드되었다 뜨지만 혼자 알아서 잘 했다.

회사에서 진행하고 있는 큰 프로젝트에 적용해보아야겠다.
