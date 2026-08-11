# Node scheduler

[npm: node-schedule](https://www.npmjs.com/package/node-schedule)

실무 프로젝트에서 node scheduler 라는모듈을 사용중이다.

근데 좀 구리다… node가 재시작 되면 해당 스케쥴러를 다시 돌려줘야한다.

서버가 다시 올라올때마다 실행시켜주는것이 있을테지만 차라리 linux의crontab을사용하는게 더 나을거 같다.

주요기능

크론 스타일의 스케줄링 : unix 크론스케줄 형식을 사용하여 작업을 예약할 수 있다.

일회성 작업 : 특정 시간에 한번만 실행되는 작업을 예약할 수 있다.

시간대 지원 : 특정 시간대에 따라 작업을 예약할 수 있다.

### 설치

```jsx
npm install node-schedule
```

### 사용예시

크론 스타일 스케줄링

```jsx
const schedule = require('node-schedule');

// 매 분 30초마다 작업 실행
const job = schedule.scheduleJob('30 * * * * *', function(){
  console.log('매 분 30초마다 이 메시지가 출력됩니다.');
});
```

특정 날짜와 시간에 작업 예약

```jsx
const schedule = require('node-schedule');

const date = new Date(2024, 5, 7, 14, 30, 0); // 2024년 6월 7일 오후 2시 30분
const job = schedule.scheduleJob(date, function(){
  console.log('지정된 날짜와 시간에 이 메시지가 출력됩니다.');
});
```

따로 console.log를 찍지 않으면 남겨지는 로그는 없다…

console.log를 찍고 pm2 log에서 보면 된다..? 좀 찜찜한 모듈
