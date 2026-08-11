# 쿼리 정렬 sort

[cursor.sort()](https://www.mongodb.com/docs/manual/reference/method/cursor.sort/)

MongoDB의 **`sort()`** 메서드는 쿼리 결과를 정렬하는 데 사용됩니다.

이 메서드는 쿼리에 대한 결과를 지정된 필드(들)를 기준으로 오름차순(ascending) 또는 내림차순(descending)으로 정렬합니다.

```bash
db.collection.find().sort({ field: 1 }) // 오름차순 정렬
db.collection.find().sort({ field: -1 }) // 내림차순 정렬
```

**`field`**는 정렬할 필드의 이름이며, **`1`**은 오름차순을 나타내고 **`-1`**은 내림차순을 나타냅니다.

다중필드 정렬도 가능합니다.

```bash
db.users.find().sort({ age: 1 }) //usrs 컬렉션에서 나이로 오름차순 정렬
db.users.find().sort({ age: -1 }) //usrs 컬렉션에서 나이로 내림차순 정렬

db.users.find().sort({ age: 1, name: -1 }) //users 컬렉션에서 나이로 오름차순, 이름으로 내림차순 정렬
```
