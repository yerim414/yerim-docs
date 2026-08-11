# Aggregate

[aggregate](https://www.mongodb.com/ko-kr/docs/manual/reference/command/aggregate/)

aggregate는 데이터를 집계하고 처리하기 위한 강력한 기능을 제공하는 집계 파이프라인이다.

aggregate를 사용하면 여러 단계로 구성된 파이프라인을 사용하여 데이터를 처리하고 결과를 반환할 수 있다.

```bash
db.collection.aggregate([
   { $match: { <조건> } }, # 문서를 필터링하여 지정된 조건에 맞는 문서만을 선택합니다.
   { $group: { _id: <그룹필드>, <집계연산자>: <필드> } }, # 문서를 그룹화하고 지정된 그룹 필드를 기준으로 집계 연산을 수행합니다.
   { $sort: { <정렬필드>: <정렬방향> } }, # 결과 문서를 정렬합니다.
   { $limit: <제한갯수> }, # 결과 문서의 개수를 제한합니다.
   { $project: { <필드>: <프로젝션값>, ... } }, # 결과 문서의 필드를 선택하거나 생성합니다.
   // 추가적인 단계들...
])
```

**`$`** 기호로 시작하는 집계 연산자를 사용합니다. 파이프 라인의 배열 순서대로 가공된다.

### aggreate 예시

```bash
db.users.aggregate([
   { $match: { status: "active" } },
   { $group: { _id: "$city", user_count: { $sum: 1 } } }
])
```

사용자가 "active" 상태인 문서를 필터링하고, 각 사용자의 도시(city)별로 그룹화한 후, 해당 도시의 사용자 수를 카운트

```bash
db.products.aggregate([
   { $sort: { price: -1 } },
   { $limit: 5 }
])
```

판매 상품 중에서 가격(price)이 가장 높은 상위 5개를 가져옴

```bash
db.users.aggregate([
   { $project: { age: { $subtract: [2024, { $year: "$birthdate" }] } } },
   { $group: { _id: "$age", user_count: { $sum: 1 }, avg_age: { $avg: "$age" } } }
])
```

사용자의 생년월일(birthdate)을 기반으로 연령대 별로 그룹화하고, 각 연령대의 사용자 수와 평균 연령을 계산
