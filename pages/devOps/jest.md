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

### 5. Snapshot 테스트

Jest는 스냅샷(Snapshot) 기능을 제공하여, 테스트 결과를 기록하고 이후 변경 사항을 검사하는 방식으로 테스트를 수행할 수 있습니다. 스냅샷 테스트를 활용하여 컴포넌트 렌더링 결과, JSON 데이터 등의 변화를 간단하게 확인할 수 있습니다.

하지만 정확한 이해가 되지 않아 테스팅 방법에 대해서 다시 한번 정리를 해보겠습니다.
