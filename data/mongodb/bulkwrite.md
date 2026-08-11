# bulkWrite()

[db. 컬렉션.bulkWrite() - 데이터베이스 매뉴얼 v8.0 - MongoDB Docs](https://www.mongodb.com/ko-kr/docs/manual/reference/method/db.collection.bulkWrite/)

bulkWrite는 대량의 데이터를 한번에 처리할수 있는 명령어

삽입만 하는게 아니라 insert, delete, update를 한번에 가능

bulkWrite의 유효한 연산 작업

- insertOne
- updateOne
- updateMany
- deleteone
- deleteMany
- replaceOne

```python
requests = [
    InsertOne({"name": "홍길동", "age": 30}),
    InsertOne({"name": "이순신", "age": 45}),
    UpdateOne({"name": "홍길동"}, {"$set": {"age": 31}}),
    DeleteOne({"name": "이순신"})
]

result = collection.bulk_write(requests)
```

orederd 옵션

기본적으로 작업은 순서대로 실행된다.

위 예시에서 orderd 옵션은 기본값 true를 가지고 있다. 그리하여 위 예제 소스는 연산이 순서대로 이루어짐

```python
result = collection.bulk_write(requests, ordered = False)
```

ordered 옵션을 false로 주게 되면 작업은 병렬로 실행하게 된다. 그리고 오류가 발생하더라도 나머지 연산의 작업은 계속 실행함

참고로 ordered True 일때보다 Fasle일때가 작업이 빠르다. 병렬작업이니까.
