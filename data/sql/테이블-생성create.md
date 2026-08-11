# 테이블 생성(CREATE)

Mysql에서 테이블을 생성할 때 Create 문을 사용합니다.

```sql
CREATE TABLE 테이블이름 (
    컬럼이름1 데이터타입1 [제약조건1],
    컬럼이름2 데이터타입2 [제약조건2],
    ...
    [테이블레벨제약조건],
    ...
);
```

- **`테이블이름`**은 생성할 테이블의 이름을 나타냅니다.
- **`컬럼이름`**은 각 열의 이름을 나타냅니다.
- **`데이터타입`**은 해당 열이 저장할 데이터의 종류를 나타냅니다. (예: VARCHAR, INT, DATE 등)
- **`제약조건`**은 열에 적용할 제약을 나타냅니다. (예: NOT NULL, UNIQUE, FOREIGN KEY 등)

---

## 데이터 타입 종류

### 숫자형 타입

| **INT** | 정수형 (양수, 음수, 0) |
| --- | --- |
| **TINYINT** | 작은 정수형 |
| **SMALLINT** | 작은 정수형 |
| **MEDIUMINT** | 중간 정수형 |
| **BIGINT** | 큰 정수형 |
| **FLOAT** | 부동 소수점 숫자 |
| **DOUBLE** | 더 큰 범위의 부동 소수점 숫자 |
| **DECIMAL** | 고정 소수점 숫자 |

### 문자형 타입

| **CHAR** | 고정 길이 문자열 |
| --- | --- |
| **VARCHAR** | 가변 길이 문자열 |
| **TEXT** | 긴 텍스트 데이터 |
| **BLOB** | 이진 데이터 (이미지, 영상 등) |
| **ENUM** | 주어진 목록에서 선택하는 문자열 |

### 날짜와 시간

| **DATE** | 날짜 |
| --- | --- |
| **TIME** | 시간 |
| **DATETIME** | 날짜와 시간 |
| **TIMESTAMP** | 날짜와 시간 (보통 현재 시간을 기준으로 자동 업데이트됨) |
| **YEAR** | 연도 |

---

## USER 테이블 생성 예시

```sql
CREATE TABLE USER (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

1. 테이블 컬럼으론 `id`, `username`, `email`, `create_at` 총 4개가 있습니다.
2. `id` 컬럼은 테이블의 PRIMARY KEY(기본키) 이고 데이터 타입은 INT형입니다. AUTO_INCREMENT로 자동으로 숫자 데이터가 증가합니다.
3. `username` 컬럼의 데이터 타입은 VARCHAR(50)이고 NOT NULL 제약조건을 가집니다.
4. `email` 컬럼의 데이터 타입은 VARCHAR(100)이고 UNIQUE 제약조건을 가집니다.
5. `created_at` 컬럼은 데이터 타입은 TIMESTAMP 이고 새로운 행(row)이 삽입될 때, 해당 열(column)에 대한 기본값으로 현재 시간을 자동으로 할당합니다.
