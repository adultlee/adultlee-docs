# Array 메서드 정리

Array에는 다양한 메서드들이 존재합니다.
다만 모든 메서드들을 모든 순간에 사용하는 것은 다소 어려운 일일지도 모릅니다.

지금은 코딩테스트를 준비하며, 제가 생각하기에 유용한 메서드들을 작성해보겠습니다.

> [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)

# Array.splice

splice() 메서드는 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 배열의 내용을 변경합니다.

예를 들어, 한 코딩 테스트 문제에서는 특정 조건을 만족하는 배열의 요소를 삭제하고, 그 자리에 새로운 요소들을 삽입하는 복잡한 작업을 수행해야 했습니다. 이때 splice() 메서드를 활용한 접근 방식은 문제를 보다 쉽게 풀어 낼 수 있도록 합니다.

```js
// 배열에서 특정 값이 있는 모든 요소 제거하기
let numbers = [1, 2, 3, 4, 5, 3, 3];
let index = numbers.indexOf(3);

while (index !== -1) {
	numbers.splice(index, 1);
	index = numbers.indexOf(3);
}

console.log(numbers); // [1, 2, 4, 5]
```

여기서 3이라는 값을 가진 모든 요소를 배열에서 효과적으로 제거합니다.

```js
// 배열의 특정 위치에 여러 요소 추가하기
let fruits = ["apple", "banana", "cherry"];
fruits.splice(2, 0, "orange", "pear");

console.log(fruits); // ['apple', 'banana', 'orange', 'pear', 'cherry']
```

이 예제는 중간에 새로운 요소를 삽입하는 상황을 보여줍니다.

```js
// 배열의 특정 부분을 다른 요소들로 교체하기
let months = ["Jan", "March", "April", "June"];
months.splice(1, 1, "Feb", "March");

console.log(months); // ['Jan', 'Feb', 'March', 'April', 'June']
```

# indexOf

내가 원하는 특정 요소가 있는지, 없는지 판단하는데 극히 유리합니다.

원하는 요소 "들" 이 중복으로 있는 경우에는 유리하지 않습니다. 첫번째 인자만 반환하기 떄문이고
이때는 map 과 같은 다른 고차함수를 섞어서 사용해야합니다.

비슷하게도 findIndex라는 메서드가 있습니다만, 아무래도 indexOf의 간편함 덕분에 좀 더 자주 사용하게 됩니다.

```js
// 조건에 맞는 첫 번째 요소의 인덱스 찾기
let fruits = ["apple", "banana", "cherry", "date"];
let target = "cherry";
let targetIndex = fruits.indexOf(target);

if (targetIndex !== -1) {
	console.log(`Found ${target} at index ${targetIndex}`); // Found cherry at index 2
} else {
	console.log(`${target} not found in the array.`);
}
```

다음과 같은 방식으로 사용합니다.

# join + split 조합

join 메서드는 하나의 array의 모든 요소들을 합쳐서 하나의 string으로 전환합니다. 이 때 join의 인자로 어떤 특정한 값을 넣냐에 따라 문자열의 방식이 바뀌곤 합니다.

제가 사용한 방식으로는 특정한 2차원 배열에서 동일한 구성의 배열들을 new Set으로 모두 간추리기 위할때 사용했습니다.
이때 join으로 모든 요소를 합쳐주고 이를 new Set으로 정렬하여 중복되는 요소를 제거하곤 했습니다.

join과 split의 조합을 사용하면, 특정 경우 배열에서 splice와 비슷한 효과를 내기도 합니다.
오히려 전체 배열에서 제거하므로 더욱 효과적이기도 할 수 있습니다.

예를 들어 A라는 배열에 a,b,a,a,a 와 같은 원소가 있을때, 이를 join().split("a")로 제거하게 되면 해당 배열의 a요소는 모두 제거 되어 다시 b만 남도록 만들 수도 있습니다.
