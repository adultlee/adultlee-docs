# js에서 ... 연산자 사용법

js에서 ...연산자는 Spread operator , Rest Operator 두 가지 방식으로 사용될 수 있습니다.
제가 주로 사용하던 방법은 다음과 같인 새로운 배열에 깊은 복사를 통해서 값을 반환하기 위해서 주로 사용하곤 했습니다.

```js
const copiedArray = [...originalArray];
```

하지만 이 방식의 경우 originalArray 배열이 depth가 깊어지게 되면 오히려 얕은 복사(주소값만을 복사)가 일어나곤 합니다.

대표적으로는 originalArray 2중 배열의 경우 새롭게 할당한 array가 originalArray 2차 배열의 주소값을 참조하게 되어, copiedArray 원소의 값의 변화가 발생했을때, originalArray 동일한 변화가 이루어지곤 합니다.
이를 해결하기 위해서는 재귀함수를 통해서 originalArray 배열의 모든 요소를 deep copy해주어야 합니다.

```js
function deepCopyArray(arr) {
	// 배열이 아닌 경우, 해당 요소 그대로 반환 (재귀 종료 조건)
	if (!Array.isArray(arr)) {
		return arr;
	}

	// 새로운 배열을 생성하여 재귀적으로 요소들을 복사
	const copiedArray = [];
	for (let i = 0; i < arr.length; i++) {
		copiedArray.push(deepCopyArray(arr[i]));
	}

	return copiedArray;
}

const originalArray = [1, [2, 3], [4, [5, 6]]];
const copiedArray = deepCopyArray(originalArray);

console.log(originalArray); // 원본 배열 출력: [1, [2, 3], [4, [5, 6]]]
console.log(copiedArray); // 깊은 복사된 배열 출력: [1, [2, 3], [4, [5, 6]]]

// 원본 배열과 복사된 배열은 서로 독립적인 객체
originalArray[1][0] = 999;
console.log(originalArray); // 원본 배열 출력: [1, [999, 3], [4, [5, 6]]]
console.log(copiedArray); // 깊은 복사된 배열 출력: [1, [2, 3], [4, [5, 6]]]
```

위는 다음과 같은 함수에 대해서 깊은복사를 수행한 경우 입니다.

저는 보통 제가 가진 어떤 배열의 원소를 옮기면서, 태초의 배열의 주소값이 const로서 선언된 경우 다음과 같은 방법을 수행합니다.

```js
// 기존의 다소 무식한 사용방법
const origin = [1, 2, 3, 4, 5];
const array = []; // 이미 선언되어 주소값을 바꿀수 없습니다. -> 즉 재할당이 불가능합니다.
for (let i = 0; i < origin.length; i++) {
	array.push(origin[i]);
}
```

```js
// 새로운 사용방법
const origin = [1, 2, 3, 4, 5];
const array = []; // 이미 선언되어 주소값을 바꿀수 없습니다. -> 즉 재할당이 불가능합니다.
array.push(...origin); // <-굉장히 깔끔하게 진행됨!
```

다음과 같이 ...(spread operator)를 사용하게 되면 아주 잘 정리가 되는 것을 확인할 수 있습니다.
아래는 다른 사용방법들입니다.

```js
// 객체의 활용방법
const obj1 = { x: 1, y: 2 };
const obj2 = { z: 3 };

// 객체를 확산 연산자를 사용하여 병합
const combinedObj = { ...obj1, ...obj2 }; // 결과: { x: 1, y: 2, z: 3 }
```

```js
function myFunction(a, b, c) {
	console.log(a + b + c);
}

const args = [1, 2, 3];

// 함수 호출 시, 확산 연산자를 사용하여 배열의 요소를 함수의 인자로 전달
myFunction(...args); // 출력: 6
```

```js
function myFunction(a, b, ...rest) {
	console.log(a); // 첫 번째 인자 출력
	console.log(b); // 두 번째 인자 출력
	console.log(rest); // 나머지 인자들을 배열로 출력
}

myFunction(1, 2, 3, 4, 5);
// 출력:
// 1
// 2
// [3, 4, 5]
```
