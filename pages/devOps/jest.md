# Jest 란

Jest는 자바스크립트와 리액트 애플리케이션을 테스트하기 위한 강력하고 사용하기 쉬운 테스팅 프레임워크입니다. Jest는 Facebook에서 개발되었으며, 단위 테스트, 통합 테스트, 스냅샷 테스트 등 다양한 테스트 유형을 지원하여 코드의 품질과 안정성을 보장하는 데에 도움이 됩니다. 이제 Jest의 주요 기능과 사용 방법에 대해 설명하겠습니다.

## Jest의 주요 기능

1. 간편한 설정: Jest는 기본 설정으로 작동하기 때문에 별도의 설정 없이 바로 사용할 수 있습니다. 하지만 사용자의 요구에 맞게 커스터마이징할 수도 있습니다.

2. 자동 Mocking: Jest는 모듈 간의 의존성을 자동으로 모의(mocking)하여 테스트를 단순화하고 테스트 실행 속도를 높입니다.

3. 풍부한 Matchers: Jest는 다양한 Matchers를 제공하여 기대 결과와 실제 결과를 쉽게 비교할 수 있습니다. 예를 들어, .toBe(), .toEqual(), .toContain() 등의 Matchers가 있습니다.

4. 비동기 테스트 지원: Jest는 비동기 코드를 테스트하기 위해 async/await나 Promise를 쉽게 처리할 수 있습니다.

5. Code Coverage 지원: Jest는 코드 커버리지를 측정하여 얼마나 많은 코드가 테스트되었는지 확인할 수 있습니다.

6. 스냅샷 테스트: Jest는 컴포넌트의 출력 결과나 JSON 데이터와 같이 변하는 결과에 대한 스냅샷 테스트를 지원합니다.

## Jest 사용 예제

### 설치 및 기본 설정

Jest를 사용하기 위해 먼저 프로젝트에 Jest를 설치해야 합니다. npm을 사용하는 경우 다음 명령어를 실행합니다:

> npm install jest --save-dev
> Jest를 설치한 뒤에는 package.json에 "jest": {}를 추가하여 기본 설정을 정의할 수 있습니다.

### 간단한 테스트 작성

Jest를 사용하여 간단한 함수를 테스트하는 예제입니다. 다음은 sum.js 파일에 있는 두 숫자를 더하는 함수를 테스트하는 코드입니다.

javascript

```js
// sum.js
function sum(a, b) {
	return a + b;
}
```

module.exports = sum;

```js
// sum.test.js
const sum = require("./sum");

test("adds 1 + 2 to equal 3", () => {
	expect(sum(1, 2)).toBe(3);
});
```

### 비동기 코드 테스트

비동기 함수를 테스트하는 예제입니다. 다음은 fetchData.js 파일에 비동기 함수를 정의하고, 해당 함수를 테스트하는 코드입니다.

```js
// fetchData.js
function fetchData() {
	return new Promise((resolve, reject) => {
		setTimeout(() => {
			resolve("Data fetched successfully!");
		}, 1000);
	});
}

module.exports = fetchData;
```

```js
// fetchData.test.js
const fetchData = require("./fetchData");

test("fetchData returns correct data", async () => {
	const data = await fetchData();
	expect(data).toBe("Data fetched successfully!");
});
```

결론
Jest는 강력하고 사용하기 쉬운 자바스크립트 테스팅 프레임워크로, 단위 테스트와 통합 테스트를 효과적으로 수행하며 코드의 안정성과 신뢰성을 높이는 데에 도움이 됩니다. Jest의 간편한 설정, 자동 Mocking, Matchers, 비동기 테스트 지원 등의 다양한 기능은 개발자들이
