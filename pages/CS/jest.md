# jest란?

Jest는 JavaScript와 TypeScript 애플리케이션을 테스트하기 위한 인기 있는 테스트 프레임워크입니다. Jest의 사용법을 간단히 설명해드리겠습니다.

### 1. Jest 설치

Jest를 사용하기 위해서는 먼저 프로젝트에 Jest를 설치해야 합니다. npm 또는 yarn을 사용하여 설치할 수 있습니다.

```bash
npm install jest --save-dev
```

또는

```bash
yarn add jest --dev
```

### 2. 테스트 파일 작성

Jest를 사용하여 테스트를 작성할 때, 테스트 파일은 일반적으로
.test.js 또는 .spec.js 확장자를 가지도록 작성하는 것이 일반적입니다.  
예를 들어,  
myFunction.js를 테스트하는 파일은 myFunction.test.js와 같이 작성합니다. 테스트 파일에서는 테스트할 코드의 함수 또는 모듈을 불러오고, 테스트 케이스를 작성합니다.

```js
// myFunction.js (테스트 대상 모듈)
function add(a, b) {
	return a + b;
}

// myFunction.test.js (테스트 파일)
const { add } = require("./myFunction");

test("덧셈 함수 테스트", () => {
	expect(add(2, 3)).toBe(5);
});
```

### 3. 테스트 실행

테스트를 실행하기 위해서는 터미널에서 다음 명령을 실행합니다.

`npx jest`

또는, package.json 파일의 scripts 섹션에 Jest 실행 명령을 추가하여 테스트를 실행할 수도 있습니다.

```json
// package.json
{
	"scripts": {
		"test": "jest"
	}
}
```

그리고 다음 명령으로도 실행 가능합니다.

```bash
npm test
```

Jest는 테스트 파일을 자동으로 탐지하고 실행하여 결과를 보여줍니다.

### 4. 기본적인 Matcher

Jest에서 테스트 결과를 판별하기 위해 사용되는 Matcher 함수들이 있습니다. 흔히 사용되는 Matcher 함수들은 다음과 같습니다.

- expect(value).toBe(expected): value가 expected와 정확히 일치하는지 확인합니다.
- expect(value).toEqual(expected): 객체나 배열 등 value가 expected와 동일한지 확인합니다.
- expect(value).toBeTruthy(): value가 truthy한 값인지 확인합니다.
- expect(value).toBeFalsy(): value가 falsy한 값인지 확인합니다.
- expect(value).toBeNull(): value가 null인지 확인합니다.
- expect(value).toBeDefined(): value가 정의되어 있는지 확인합니다.
- expect(value).toBeUndefined(): value가 undefined인지 확인합니다.
- expect(value).toContain(item): 배열이나 문자열에 item이 포함되어 있는지 확인합니다.
- expect(value).toHaveLength(length): 배열 또는 문자열의 길이가 length와 일치하는지 확인합니다.
- expect(value).toHaveProperty(propertyName): 객체가 propertyName을 가지고 있는지 확인합니다.

  이 외에도 Jest는 다양한 Matcher 함수들을 지원하므로, 프로젝트에 맞게 적절한 Matcher를 사용할 수 있습니다.

### 6. 그래서 내가 사용한 방법은?

```js
// equal 테스트
const TESTCLASS = require("./index.js");

describe("TESTCLASS  테스트", () => { // 내가 묶어서 사용할 테스트 모음집 여러 테스트들을 하나의 규칙으로 묶어서 사용가능
	test("value와 name을 테스트합니다", () => { // value와 name을 테스트 하겠다는 명시, 개발자가 이해하기 적합한 제목을 사용하는것이 좋다
		const path = new TESTCLASS("value"); // 이 부분은 내가 원하는 class를 선언하거나 코드를 작성하는 부분
		expect({ // 여기서 path가 과정을 거쳐서, 어떤 반환값을 가지게 되는지 확인
			value: path.value,
			name : path.name
		}).toEqual({ // 여기는 strict 하게 내가 사용할 값이 제대로 나오는지 확인해야 한다.
			value: "value", // 직접 입력
			name : "이성인", // 직접 입력
		});
	});
```

```js
// 잘못된 입력인지 확인
test("잘못된 입력인지 확인", () => {
	expect(() => new TESTCLASS("@@@@@@@@@@@@@@@@@@@@")).toThrow(
		"잘못된 입력입니다."
	);
});
```

```js
//if(입력값이 @가 포함되어 있다면?)
throw new Error("잘못된 입력입니다.");
```

## 추가 메모 사항

1. 각 test의 상태는 완벽히 독립적이다.
2. test를 진행하기 전에, 항상 필요한 정리를 해두어야 한다. (배열을 셋팅해둔다거나...)
3. test에서 호출한 함수의 내부 함수에 대해서는 추가로 선언하지 않아도, jest가 찾아서 실행시킨다.
