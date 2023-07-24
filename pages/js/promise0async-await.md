# promise객체를 사용하는 방법과 async await방법을 사용하는 방법의 차이

두 방법모두 js에서 비동기 처리를 수행하기 위해서 도입된 문법입니다.
하지만 async/await 문법은 Promise를 기반으로 하면서 비동기적인 작업을 보다 동기적으로 처리하기 위해서 ES2017에 도입된 문법입니다. async 함수 내부에서 await 키워드를 사용해서 비동기 작업이 완료될때까지 기다린 후 결과를 받아올 수 있습니다. 이를 통해서 비동기 처리를 좀더 직관적이고 동기적인 구조로 작성할 수 있습니다.

```js
// 예시: async/await를 사용한 비동기 작업
async function fetchData() {
	// 비동기 작업 수행
	// 비동기 작업이 완료되면 결과를 반환
}

// async/await를 사용한 비동기 작업의 결과 처리
async function processData() {
	try {
		const result = await fetchData(); // 비동기 작업이 완료될 때까지 대기하고 결과를 받아옴
		// 성공적인 결과 처리
	} catch (error) {
		// 오류 처리
	}
}
```
