# commit 메세지 작성

[[Git] Commit Message Convention](https://velog.io/@archivvonjang/Git-Commit-Message-Convention)

https://github.com/angular/angular/blob/main/contributing-docs/commit-message-guidelines.md

커밋 메세지는 “무엇을 했는지”가 아니라 “무엇이 변경되었는지” 설명해야함

커밋 메세지는 명령문 형태

1. 커밋 메시지 구조 (Conventional Commits 권장)

```python
<타입>(옵션:영역): <변경 요약>
[공백]
(옵션) 변경 상세 설명 (본문)
[공백]
(옵션) 관련 이슈 번호
```

```python
feat(auth): 로그인 기능 구현

- JWT 기반 로그인 구현
- 비밀번호 해싱 및 검증 추가

Refs: #15
```

1. 커밋 타입 분류

| 타입 | 설명 |
| --- | --- |
| `feat` | 새로운 기능 추가 |
| `fix` | 버그 수정 |
| `docs` | 문서 변경 (README, 주석 등) |
| `style` | 코드 포맷팅, 세미콜론 누락 등 (기능 변경 없음) |
| `refactor` | 리팩토링 (기능 변경 없음) |
| `test` | 테스트 코드 추가/수정 |
| `chore` | 빌드/배포/도구 설정 관련 작업 |
| `perf` | 성능 개선 |

그 외 팀 commit 규칙이 있다면 그에 따른다.
