# 로컬 MCP 연결 - DB연결

mcp서버를 연결해서 DB연결을 해보겠습니다

로컬DB는 Posgtresql로 이용한다

1. 사전준비\
   먼저 내 로컬에 Claude Desktop 앱, PostgresSQL, Node.js 설치가 되어 있어야 한다.\
   그리고 연습에 사용할 DB Table도 하나 만들어 준다

```sql
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    price NUMERIC(10, 2),
    stock INTEGER DEFAULT 0,
    created_at TIMESTAMP DEFAULT NOW()
);

INSERT INTO products (name, price, stock) VALUES
('키보드', 89000, 15),
('마우스', 32000, 40),
('모니터', 250000, 7);
```

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

1. Claude가 사용할 계정 만들기

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

먼저 Claude가 사용할 읽기 전용 계정을 하나 만들어 준다.

```sql
-- 1) 계정 생성 (서버 전체에 하나만 있으면 됨)
CREATE USER claude_reader WITH PASSWORD '원하는_비밀번호';

-- 2) study 데이터베이스에 접속할 권한
GRANT CONNECT ON DATABASE study TO claude_reader;

-- 3) public 스키마를 들여다볼 권한
GRANT USAGE ON SCHEMA public TO claude_reader;

-- 4) 현재 존재하는 모든 테이블 조회 권한
GRANT SELECT ON ALL TABLES IN SCHEMA public TO claude_reader;

-- 5) 앞으로 새로 만들 테이블에도 자동으로 조회 권한 부여
ALTER DEFAULT PRIVILEGES IN SCHEMA public
  GRANT SELECT ON TABLES TO claude_reader;
```

계정 생성 및 권한까지 부여 한다.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

SELECT 즉 읽기 권한만 받은 상태!

1. MCP 서버 고르기\
   Anthropic이 초기에 배포했던 `@modelcontextprotocol/server-postgres`는 **더 이상 유지보수되지 않으며 SQL 인젝션 취약점이 알려져 있습니다.**

| 서버                         | 특징                                                          |
| -------------------------- | ----------------------------------------------------------- |
| `mcp-server-pg`            | 트랜잭션 레벨에서 읽기 전용을 강제 — SQL 인젝션으로 우회 불가. 스키마 조회, 마이그레이션 보조 지원 |
| `@crystaldba/postgres-mcp` | 읽기 전용 접근 + 스키마 검사 + 쿼리 성능 분석 기능 포함                          |

나는 `mcp-server-pg` 를 사용!

1. 클로드 설정 파일 위치 확인\
   다음은 클로드 데스크톱을 설치하면서 생긴 설정파일을 확인해야한다

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

개발자의 구성편집 버튼을 누르면 바로 claude\_desktop\_config.json 가 설치된 경로로 파일탐색기가 열린다

```sql
"C:\Users\user\AppData\Local\Packages\Claude_pzs8sxrjxfjjc\LocalCache\Roaming\Claude\claude_desktop_config.json"
```

다른 블로그에서 적어둔 경로랑은 다르기 때문에 위와 같은 방법으로 경로 찾는걸 추천한다.

**경로가 다른 이유가 Microsoft Store에서 다운받은거라 일반 설치판과는 경로가 다르다고한다.**

```sql
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-server-pg",
        "--connection-string",
        "postgresql://claude_reader:비밀번호@localhost:5432/study",
        "--read-only"
      ]
    }
  }
}
```

아무튼 해당 json 파일에 위 내용을 추가한다.

1. 연결 확인\
   클로드를 완전히 종료 하고 다시 실행해보면

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

정상적으로 포스트 그레스가 추가 되었다!

그리고 다음과같이 질문을 해봣는데

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

아까 생성한 데이터들을 정상적으로 읽어오고 있다!
