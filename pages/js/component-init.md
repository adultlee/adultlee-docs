# React에서 컴포넌트 선언방식

React에서 컴포넌트를 정의하는 방식에는 크게 두 가지가 있습니다.
<b>화살표 함수(const Component = () => {})</b>를 사용하는 방식과 <b>일반 함수 선언(function Component() {})</b>을 사용하는 방식입니다.

두 방식 모두 유효하며, React 컴포넌트를 정의하고 사용할 수 있습니다. 그렇지만 두가지 방식에는 몇가지 차이가 있습니다.

```js
// 화살표 함수를 사용하여 컴포넌트를 정의
const ArrowFunctionComponent = () => {
	// 화살표 함수 내부에서 JSX를 반환합니다.
	return <div>Hello, this is a component defined by an arrow function!</div>;
};
```

```js
// 일반 함수 선언을 사용하여 컴포넌트를 정의
function FunctionDeclarationComponent() {
	// 함수 내부에서 JSX를 반환합니다.
	return (
		<div>Hello, this is a component defined by a function declaration!</div>
	);
}
```

### 문법과 가독성

화살표 함수는 ES6에 도입된 더 짧고 간결한 문법을 제공합니다. 이는 코드를 더 간결하게 만들고 가독성을 향상시킬 수 있습니다. 반면에 일반 함수 선언은 조금 더 전통적이고 명시적인 방법입니다.

### this 바인딩

일반 함수와 화살표 함수의 가장 큰 차이점 중 하나는 <b>this 바인딩 방식</b>입니다. 일반 함수에서 this는 함수가 호출되는 방식에 따라 달라집니다. 반면, 화살표 함수에서 this는 함수가 선언될 때의 컨텍스트를 유지합니다. 하지만 React의 함수형 컴포넌트에서는 컴포넌트의 메서드나 생명주기 메서드를 다루지 않기 때문에, 이 차이가 컴포넌트 정의에 큰 영향을 미치지는 않습니다.

### 생성자 함수 사용

일반 함수 선언을 사용하면 그 함수를 생성자 함수로 사용할 수 있습니다. 즉, new 키워드를 사용하여 인스턴스를 생성할 수 있습니다. 화살표 함수는 생성자 함수로 사용할 수 없습니다. 하지만 React 컴포넌트에서는 일반적으로 생성자 함수를 사용하지 않으므로, 이 차이점이 실제로 중요하지 않을 수 있습니다.

### 호이스팅

일반 함수 선언은 호이스팅됩니다. 즉, 함수 선언 전에도 해당 함수를 호출할 수 있습니다. 반면에 화살표 함수는 const나 let으로 선언된 변수에 할당되므로 호이스팅되지 않습니다. 이는 컴포넌트의 구조와 로딩 순서에 영향을 줄 수 있습니다.

### 컴포넌트 이름 추론

개발 도구에서 컴포넌트의 이름을 자동으로 추론할 때, 화살표 함수는 함수의 이름을 변수 이름에서 추론합니다. 반면, 일반 함수 선언은 함수 이름 자체를 사용합니다. 이는 디버깅 시 유용할 수 있습니다.

결론적으로, 두 방식 사이에는 몇 가지 기술적 차이가 있지만, React 컴포넌트를 정의하는 데 있어서는 주로 개인의 선호나 프로젝트의 스타일 가이드에 따라 결정됩니다. 함수형 컴포넌트에서는 this 바인딩이 큰 이슈가 되지 않기 때문에, 두 방식 중 어느 것을 사용해도 대부분의 경우 문제가 되지 않습니다.

- 화살표 함수 컴포넌트: 화살표 함수로 컴포넌트를 정의하면, 컴포넌트의 이름은 변수 이름에서 추론됩니다. 예를 들어, `const MyComponent = () => <div />;`라고 정의한 경우, 개발 도구는 컴포넌트의 이름을 MyComponent로 추론합니다.
- 함수 선언 컴포넌트: 함수 선언으로 컴포넌트를 정의하면, 컴포넌트의 이름은 함수 이름에서 직접 추론됩니다. 예를 들어, `function MyComponent() { return <div />; }`라고 정의한 경우, 이 함수 이름이 곧 컴포넌트 이름으로 사용됩니다.

# 더 생각해볼 점

함수 이름 추론: 함수 선언 방식은 함수의 이름을 명시적으로 제공합니다. 이는 디버깅 시 스택 트레이스에서 해당 함수를 식별하기 쉽게 만들어 줍니다. 반면, 화살표 함수는 익명 함수로 사용될 때 함수 이름을 가지지 않을 수 있으며, 이는 디버깅을 어렵게 만들 수 있습니다. 그러나 화살표 함수를 변수에 할당할 때는 변수 이름을 통해 이름을 추론할 수 있으므로, 이러한 문제를 일정 부분 해결할 수 있습니다.

호이스팅: 함수 선언은 호이스팅되어, 코드의 어느 위치에서든지 호출할 수 있습니다. 이는 프로그램의 흐름을 분석할 때 유용할 수 있습니다. 반면, 화살표 함수는 변수에 할당되기 전에는 사용할 수 없어, 초기화 순서에 대한 오류를 디버깅할 때 추가적인 고려가 필요할 수 있습니다.

그럼에도 불구하고, 현대의 JavaScript 개발 환경에서는 소스맵과 같은 도구를 통해 화살표 함수와 함수 선언 방식 모두 효과적으로 디버깅할 수 있습니다. 따라서, 디버깅의 용이성은 크게 함수 정의 방식에 의존하지 않으며, 개발자의 선호나 프로젝트의 스타일 가이드를 따르는 것이 좋습니다.

## 요약

요약하자면, 함수 선언 방식이 몇 가지 경우에 디버깅에 유리할 수 있지만, 현대 개발 도구의 지원으로 인해 두 방식 사이의 차이는 크게 중요하지 않을 수 있습니다. 가장 중요한 것은 코드의 일관성과 가독성을 유지하며, 개발자가 이해하고 사용하기 편한 방식을 선택하는 것입니다.

## 두 환경에서 디버깅은 거의 동일

-> 아마 개발 환경이 발전하면서 기존의 editor에서 발생할 수 있는 문제가 개선된듯

<img src="https://private-user-images.githubusercontent.com/77886826/309725102-9d3b4468-b6c3-4f43-a5c3-63cc268f047a.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDk1NDk0NjMsIm5iZiI6MTcwOTU0OTE2MywicGF0aCI6Ii83Nzg4NjgyNi8zMDk3MjUxMDItOWQzYjQ0NjgtYjZjMy00ZjQzLWE1YzMtNjNjYzI2OGYwNDdhLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDAzMDQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwMzA0VDEwNDYwM1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWM1ZWVjMmIwMjdiYzhmNzY2NjZmMjZmMmY0ZjViZDY4YmUzOGYxMzc4YTZlMjc3Yzc4OGQyODA4YzA2ZTZkZGUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.6lDMrCLDD8KiChotX9LIpc5yG54jsiiECrGTGmppAZM" alt="image" style="max-width: 100%;">

<img src="https://private-user-images.githubusercontent.com/77886826/309725774-439006c3-eb99-4de0-b930-362b88e2b346.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDk1NDk1NzEsIm5iZiI6MTcwOTU0OTI3MSwicGF0aCI6Ii83Nzg4NjgyNi8zMDk3MjU3NzQtNDM5MDA2YzMtZWI5OS00ZGUwLWI5MzAtMzYyYjg4ZTJiMzQ2LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDAzMDQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwMzA0VDEwNDc1MVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWI1NWI3MGVkZjQxZmE1NTAyN2ZjYTNmMDk4NGExMDRjYTdkZjQ3ZjQ2N2Q0YzhmM2YzYjY1ZGI4MGNlYjIzN2ImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.Tpt3NKjJpk8sBvjYBWA0Yn6ml0MshCYoWHavfC-iZ-4" alt="image" style="max-width: 100%;">
