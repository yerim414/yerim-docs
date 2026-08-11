# TTL Index

[TTL Indexes](https://www.mongodb.com/ko-kr/docs/manual/core/index-ttl/)

TTL 인덱스란?

Time To Live 의 약자로 몽고데이터베이스에서 도큐먼트를 자동으로 삭제하기 위해 사용되는 인덱스이다.

TTL 인덱스가 필요한 이유

몽고디비는 한번 용량이 늘어나면 데이터를 지워도 용량을 스스로 반환하지 않는다.

용량 제한을 위한  관리가 필요하다. 그 중 하나가 TTL 인덱스 이다.

TTL 인덱스 생성 방법

```jsx
db.collection.CreateIndex({"createdAt" :1}, {expireAfterSeconds: 3600})
//createdAt 필드를 기준으로 1시간 뒤 도큐먼트 삭제
```

ExpireAfterSeconds 옵션을 사용하여 도큐먼트가 삭제될 시간(초)를 지정해야한다. 네이버에 초 계산을 이용하여 지정할 시간찾으면 편하다!!

TTL 인덱스를 지정할 필드는 DateTime으로되어 있는 컬럼이여야 한다.

**컬럼이 “2023-02-10 10:10:11” 이렇게(string) 들어있는게 아닌 리얼 데이터 타입이 DATETIME 이여야한다**

TTL은 멀티 인덱스로 구성할 수 없다

**초기 구성때 도큐먼트 생성 컬럼을 추가와 TTL 인덱스를 추가해준다 그렇지 않으면 나중에 상당히 고생한다 ㅜㅜ**

TTL과 조금 비슷한 capped도 있지만 경우에 따라 유연하게 선택하기
