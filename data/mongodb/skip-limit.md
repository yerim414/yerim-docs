# Skip, Limit

skip과 limit는 페이지네이션을 구현하는 데 사용됩니다.

**`skip()`** 메서드는 쿼리 결과에서 지정된 수의 문서를 건너뛰고 나머지 문서를 반환합니다. 보통 페이지네이션에서 이전 페이지의 결과를 건너뛰기 위해 사용됩니다.

```bash
// 10개의 문서를 건너뛴 후 나머지 문서를 반환
db.collection.find().skip(10)
```

**`limit()`** 메서드는 쿼리 결과에서 반환할 문서의 최대 수를 지정합니다. 보통 페이지네이션에서 한 페이지에 표시할 문서 수를 제한하기 위해 사용됩니다.

```bash
// 최대 10개의 문서를 반환
db.collection.find().limit(10)
```

```bash
// 2페이지의 10개 문서 반환
var result = db.collection.find().skip(10).limit(10);
```
