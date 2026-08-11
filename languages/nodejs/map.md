# Map

Map, filter, reduce가서로 비슷해서 헷갈린다

Map

Map 함수는 배열의 각 요소를 변환하여 새로운 배열을 생성합니다.

원본 배열의 길이는 유지되며, 각 요소는 주어진 함수에 의해 변환됩니다.

```jsx
const numbers = [1, 2, 3, 4, 5]
const doubled = numbers.map(num => num * 2);
console.log(doubled);

//출력값
[2, 4, 6, 8, 10]
```
