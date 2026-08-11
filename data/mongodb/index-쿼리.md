# Index 쿼리

[Indexes](https://www.mongodb.com/ko-kr/docs/v5.0/indexes/)

1. 인덱스 조회

```bash
db.user.getIndexes()

#user 컬렉션의 인덱스 조회
```

1. 인덱스 생성

```bash
db.book.createIndex({"title": 1 })

# book 컬렉션의 title 인덱스 생성(단일 필드)

db.book.createIndex({"title":1, "author":1})

# book 컬렉션의 title, author 인덱스 생성(복합 필드)

```

1. 인덱스 삭제

```bash
db.book.dropIndex({ "name": 1 })

# book 컬렉션의 name 인덱스 삭제

db.book.dropIndexes()

# book 컬렉션의 모든 인덱스 삭제
```

1. 인덱스 크기

```bash
db.user.totalIndexSize()

# usr 컬렉션의 총 인덱스 사이즈 반환 
```
