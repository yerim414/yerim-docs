# 페이징 처리(LIMIT, OFFSET)

**`LIMIT`** 및 **`OFFSET`** 절은 SELECT 문에서 결과 갯수를 지정하고 원하는 행부터 시작할 수 있게 하는 데 사용됩니다. 

**`LIMIT`**는 반환되는 행의 수를 제한하고, **`OFFSET`**은 시작 지점을 지정합니다.

```sql
SELECT * FROM USER LIMIT 5;
```

LIMIT를 이용하여 USER테이블에서 처음 5개의 값만 가져옵니다.

```sql
SELECT * FROM USER LIMIT 5 OFFSET 5;
```

USER 테이블에서 6번째부터 10번째 행까지의 값만 가져옵니다.

```sql
SELECT * FROM BOARD LIMIT 10 OFFSET 10;
```

게시판 기능에 페이지 네이션 기능을 추가하게 된다면 쿼리는 위와 같이 사용하면 됩니다.
한 페이지당 보여주는 게시물의 갯수는 10개 입니다.
**`OFFSET`**이 10 이므로 현재 페이지는 2 페이지 입니다.

3페이지는 20 4페이지는 30… **`OFFSET`**만 변경됩니다.
