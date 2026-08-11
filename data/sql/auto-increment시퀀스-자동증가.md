# Auto Increment(시퀀스 자동증가)

자동으로 시퀀스 값이 올라가는 것은 **자동 증가(Auto Increment)** 기능을 의미합니다. 

이는 주로 테이블의 **기본 키(primary key)** 열에 사용됩니다. 

이 열에 값을 직접 지정하지 않으면 MySQL은 자동으로 값을 할당하고 이를 1씩 증가시킵니다.

```sql
CREATE TABLE example_table (
    SEQ INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50)
);
```

`SEQ` 열은 자동 증가 기능을 가지고 있습니다. 따라서 이 열에 값을 삽입하지 않으면 MySQL이 자동으로 값을 할당하고, 새로운 행이 추가될 때마다 값이 1씩 증가합니다.

자동 증가 기능을 사용하면 테이블에 새로운 데이터를 삽입할 때마다 고유한 식별자를 생성할 수 있으므로 매우 편리합니다.

만약 해당 테이블을 값을 전부 DELETE 한 뒤 새로운 값을 INSERT하게 된다면 `AUTO_INCREMENT` 컬럼의 값은 1부터 시작되는게 아닌 삭제 되기 전 마지막 `SEQ` 값에서 +1 된 값일것입니다.

`AUTO_INCREMENT`를 초기화 하는 방법은 다음과 같습니다.

```sql
ALTER TABLE table_name AUTO_INCREMENT = 1;
```

**`AUTO_INCREMENT = 1`**을 사용합니다. 이 값을 원하는 다른 값으로 변경할 수도 있습니다.
