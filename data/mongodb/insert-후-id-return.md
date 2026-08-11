# insert() 후 _id return

[db. 컬렉션.insertOne() - 데이터베이스 매뉴얼 v8.0 - MongoDB Docs](https://www.mongodb.com/ko-kr/docs/manual/reference/method/db.collection.insertOne/)

mongodb에 insert후 _id 값을 받아야 할 때

mariaDB - backend - mongoDB의 형태인데.. mongo에 insert된 데이터를 maria db에 연동 시킬때..

```python
try {
   db.products.insertOne( { item: "card", qty: 15 } );
} catch (e) {
   print (e);
};
```

위와같이 데이터를 insert하였을때 결과값으로 아래와 같은 데이터를 받음

```python
{
   "acknowledged" : true,
   "insertedId" : ObjectId("56fc40f9d735c28df206d078")
}
```

해당 연산을 변수로 저장받아 insertedId값만 꺼내주면 됨!

```python
result = db.products.insertOne( { item: "card", qty: 15 } )

print("insertData :: ", result.insertedId)
```

insertMany도 동일하다.

```python
try {
   db.products.insertMany( [
      { item: "card", qty: 15 },
      { item: "envelope", qty: 20 },
      { item: "stamps" , qty: 30 }
   ] );
} catch (e) {
   print (e);
}
```

위와 같이 여러 데이터를 insert 시에

```python
{
   "acknowledged" : true,
   "insertedIds" : [
      ObjectId("562a94d381cb9f1cd6eb0e1a"),
      ObjectId("562a94d381cb9f1cd6eb0e1b"),
      ObjectId("562a94d381cb9f1cd6eb0e1c")
   ]
}
```

insert된 데이터의 _id 값을 배열로 받게된다
