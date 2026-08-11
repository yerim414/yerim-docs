# Reduce

Array.reduce()

Reduce 함수는 배열의 각 요소를 순회하면서, 이전 요소의 연산 결과를 다음 요소의 연산에 사용하는 누산기를 통해 하나의 값으로 줄이는 데 사용된다.

```jsx
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.redue((accumulator, currentValue) =>{
	return accumulator + crrentValue;
	}, 0);
	
	console.log(sum);
	// 15 출력
```

```jsx
const items = [
    { name: 'item1', price: 10 },
    { name: 'item2', price: 20 },
    { name: 'item3', price: 30 }
];

const totalPrice = items.reduce((accumulator, currentValue) => {
    return accumulator + currentValue.price;
}, 0);

console.log(totalPrice); // 출력: 60

```

Accumulator : 누산기, 콜백의 반환값을 누적

CurrentValue : 처리할 현재 요소

Map, filter 와 달리 reduece는값을 더해줌

그러므로 reduce의값은 단일의 값임
