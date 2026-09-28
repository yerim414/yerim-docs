# 작성 대기 중인 초안

내용이 비어 있어 [SUMMARY.md](SUMMARY.md)에서 제외한 문서 목록.
사이드바에 노출되지 않으며, 파일 자체는 남아 있다.

이 파일은 SUMMARY에 등록하지 않으므로 GitBook에 발행되지 않는다.

## 목록

| 문서 | 섹션 | 되돌릴 위치 |
|---|---|---|
| [Explain](data/sql/explain.md) | SQL | `SUMMARY.md` + `data/sql/README.md` |
| [검색로봇 차단](infra/linux/검색로봇-차단.md) | Linux | `SUMMARY.md` + `infra/linux/README.md` |
| [Unexpected token , in JSON at position](languages/nodejs/unexpected-token-in-json-at-position.md) | Node.js | `SUMMARY.md` + `languages/nodejs/README.md` |
| [scheduler](languages/python/scheduler.md) | Python / 동시성 & 스케줄링 | `SUMMARY.md` + `languages/python/groups/동시성-스케줄링.md` |
| [discord 개발자 포탈, 토큰 받기](projects/discord-bot/discord-개발자-포탈-토큰-받기.md) | 디스코드 봇 | `SUMMARY.md` + `projects/discord-bot/README.md` |
| [롤 전적 검색 봇 만들기 3](projects/discord-bot/롤-전적-검색-봇-만들기-3.md) | 디스코드 봇 | `SUMMARY.md` + `projects/discord-bot/README.md` |
| [Create api](projects/fastapi-pydantic/create-api.md) | FastAPI & Pydantic | `SUMMARY.md` + `projects/fastapi-pydantic/README.md` |

## 다시 노출하려면

1. 문서 내용을 채우고 상단의 "작성 중인 초안입니다" 안내 문구를 지운다.
2. `SUMMARY.md`의 원래 정렬 위치에 링크를 추가한다. (라틴 문자 먼저, 그다음 한글)
3. 해당 섹션의 `README.md`(또는 그룹 페이지)에도 링크를 추가한다.
4. 이 표에서 해당 행을 지운다.

## 참고

`롤 전적 검색 봇 만들기 3`은 1·2편이 내용 있는 시리즈물이라 비어 있는 것이 특히 눈에 띈다.

내용이 얇은(3~7줄) 문서들은 숨기지 않고 그대로 두었다. 지금도 최소한의 정보는 담고 있다.
[cidr.md](cs/fundamentals/cidr.md), [interview.md](cs/interview.md), [stackshare.md](cs/fundamentals/stackshare.md),
[무료-가상-api-제공-사이트.md](cs/fundamentals/무료-가상-api-제공-사이트.md),
[정규식-테스트.md](cs/fundamentals/정규식-테스트.md), [mysql-외부접속.md](data/sql/mysql-외부접속.md),
[forward-reference선행-참조-전방-참조.md](languages/python/forward-reference선행-참조-전방-참조.md),
[etc/collaboration/README.md](etc/collaboration/README.md)
