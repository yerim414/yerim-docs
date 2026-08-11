# Nosql vs sql

### sql (Relational Database, RDB)

- 구조화된 데이터, 구조화된 쿼리 언어
- 테이블, 행(Row), 열(Column) 구조.
- 엄격한 스키마. 미리 정의된 구조를 따라야만 입력이 가능하다.
- 외래키를 통해 테이블 간 관계 설정이 가능하다.
- ACID 보장 : 트랜잭션 처리에서 Atomicity, Consistency, Isolation, Durability 제공 → 데이터 안정성 높음.

대표 DB

MySQL

postgreSQL

MariaDB

Oracle

### NoSQL( Non-Relational Database)

- 유연한 데이터 구조를 지닌다. 컬렉션, 도큐먼트, 키-값 형태 등 다양하다.
- 스키마리스, 데이터 구조를 미리 정의하지 않아도 됨
- 수평적 확장이 쉬움, 대량의 데이터 처리에 유리
- CAP 특성 Consistency, Availability, Partition tolerance 중 일부 특성을 조절 가능.

종류 및 대표 DB

문서형(Document) : MongoDB, CouchDB

키-값(key-value) : Redis, DynamoDB

선택하는 기준

| 기준 | SQL | NoSQL |
| --- | --- | --- |
| 데이터 구조 | 고정 구조, 관계형 | 유연한 구조, 관계 복잡도 낮음 |
| 트랜잭션 | ACID 필수 | BASE 가능, 유연성 강조 |
| 확장성 | 수직적 확장(서버 성능 업) | 수평적 확장(노드 추가) 용이 |
| 사용 예시 | 은행, ERP, 전통 웹 앱 | 빅데이터, 로그, 실시간 채팅, SNS |

---

[How do you decide between using SQL and NoSQL databases?](https://www.reddit.com/r/webdev/comments/1gnc5dg/how_do_you_decide_between_using_sql_and_nosql/?tl=ko)

nosql과 sql을 둘다 써보았지만

mongodb를 현재 프로젝트에서 제거하고 postgre로 마이그레이션을 하는쪽으로 다들 동의하고 있다…

이유는 현재 하는 프로젝트에서 사용중인 몽고 DB는  몽고의 가장 큰  장점인 유연한 구조의 의미가 없기때문이다.

`데이터 수집 → 몽고에 저장 → 수집된 데이터 sql로 전송(전송과정에서 relation 및 데이터 유효성 확인)`

간단히는 위 순서대로 데이터 수집에서 몽고에 저장까지의 작업도 데이터 파싱이 이루어 지는데 그냥 바로 sql로 쏘는게 나을거 같다고 생각이 든다…

syslog만 mongo를 이용하고 그 외 수집데이터는 postgre 를 이용하는 방향으로 제안하기

결국은 돌고돌아서 sql인거같다
