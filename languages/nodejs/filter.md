# Filter

filter 함수는 배열의 각 요소에 대해 주어진 조건을 검사하여, 조건을 만족하는 요소들만 모아 새로운 배열을 생성합니다.

원본 배열의 길이는 변할 수 있습니다.

```jsx
const numbers = [1, 2, 3, 4, 5];
const evenNumbers ==numbers.filter(num => num % 2 === 0);
console.log(evenNumbers);

//출력 : [2, 4]
```
