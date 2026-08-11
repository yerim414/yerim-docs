# JSON 데이터 형식

MySQL 5.7 이상부터 JSON 데이터 형식을 지원합니다.

### json형식 컬럼을 가진 테이블 생성

```sql
CREATE TABLE PRODUCTS (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    attributes JSON
);
```

상품 테이블을 생성합니다.

`attributes` 라는 컬럼은 JSON 데이터 형식을 가지고 있습니다.

### json데이터 형식 컬럼에 INSERT

```sql
INSERT INTO products (name, attributes) VALUES ('Product 1', '{"color": "blue", "size": "small"}');
```

JSON데이터 INSERT는 일반적인 데이터 형식과 동일하게 INSERT합니다.

### JSON데이터 형식 컬럼 SELECT

JSON데이터 형식의 컬럼은 다른 SELECT와 좀 다릅니다.

JSON 데이터를 조회하는데는 일반적으로 MySQL의 JSON 함수를 사용합니다.

**`->` 연산자**

**`->`** 연산자는 JSON 객체에서 지정된 경로를 따라 특정 속성의 값을 추출합니다. 반환되는 값은 JSON 형식입니다.

```sql
SELECT column_name->'$.color' AS color_value FROM table_name;
```

**`column_name`** 열에서 JSON 객체의 **`color`** 속성의 값을 가져와 **`color_value`**라는 별칭으로 반환합니다.

**`->>` 연산자**
**`->>`** 연산자는 **`->`** 연산자와 유사하지만 반환되는 값이 JSON 형식이 아니라 문자열 형식입니다.

```sql
SELECT column_name->>'$.color' AS color_value FROM table_name;
```

**`column_name`** 열에서 JSON 객체의 **`color`** 속성의 값을 가져와 문자열 형식으로 **`color_value`**라는 별칭으로 반환합니다.

연산자를 조건절에 사용

**`WHERE`** 절에서 **`->`** 또는 **`->>`** 연산자를 사용할 수 있습니다.

```sql
SELECT * FROM table_name WHERE column_name->>'$.color' = 'blue';
```

**`column_name`** 열에서 JSON 객체의 **`color`** 속성이 'blue'인 행을 선택합니다.

이러한 연산자가 아닌 **`JSON_EXTRACT()`**  함수를 사용할 수 있습니다.

```sql
SELECT JSON_EXTRACT(column_name, '$.color') AS color_value FROM table_name;
```

**`column_name`** 열에서 JSON 객체의 **`color`** 키의 값을 가져와 **`color_value`**라는 별칭으로 반환합니다.
위에서 보았던 **`->`**  연산과 동일한 결과 입니다.

---

그럼 `->` 연산자와 `JSON_EXTRACT()` 의 차이점이 무엇인가요?

1. 사용방법
    - **`JSON_EXTRACT()`** 함수는 함수 형태로 사용됩니다. 이 함수는 첫 번째 매개변수로 JSON 데이터를 받고, 두 번째 매개변수로는 JSON 경로를 받습니다.
    - `→` 연산자는 일반적으로 SQL 문의 SELECT 절에서 사용됩니다. JSON 컬럼 이름 다음에 사용되고, JSON 경로는 문자열 리터럴로 표현됩니다.
2. 중첩된 객체 및 배열 처리
    - **`JSON_EXTRACT()`** 함수는 중첩된 JSON 객체나 배열의 값을 추출할 수 있습니다. JSON 경로를 사용하여 원하는 위치의 값을 추출할 수 있습니다.
    - **`>`** 연산자는 단일 수준의 키를 추출하는 데 사용됩니다. 따라서 중첩된 객체나 배열의 값을 추출하기 위해서는 여러 번의 **`>`** 연산자를 사용해야 합니다.
