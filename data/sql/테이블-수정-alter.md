# 테이블 수정 (ALTER)

ALTER명령어는 데이터베이스, 테이블 또는 기타 데이터베이스 객체의 구조를 변경하는데 사용됩니다.

### 테이블에 새로운 컬럼 추가

```sql
ALTER TABLE 테이블명
ADD 열이름 데이터유형;
```

USER 테이블에 email 컬럼을 추가

```sql
ALTER TABLE USER
ADD email VARCHAR(100);
```

### 테이블 컬럼 수정하기

```sql
ALTER TABLE 테이블명
MODIFY 열이름 새데이터유형;
```

USER 테이블의 email 컬럼 데이터유형 수정하기

```sql
ALTER TABLE USER
MODIFY email VARCHAR(150);
```

### 테이블 컬럼 삭제하기

```sql
ALTER TABLE 테이블명
DROP COLUMN 열이름;
```

USER 테이블의 이메일 컬럼 삭제하기

```sql
ALTER TABLE users
DROP COLUMN email;
```

### 테이블의 제약조건 추가하기

```sql
ALTER TABLE 테이블명
ADD CONSTRAINT 제약조건명 제약조건;
```

ORDERS 테이블에 customer_id 컬럼에 대해 외래키 제약 조건을 추가

```sql
ALTER TABLE orders
ADD CONSTRAINT fk_customer_id
FOREIGN KEY (customer_id)
REFERENCES customers(id);
```

ALTER 명령어는 테이블의 이름도 바꿀수 있고 VEIW 테이블의 쿼리도 변경 할 수 있습니다.
