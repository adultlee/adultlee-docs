## Regex의 이름지정 구문이란

부스트캠프 과정에서 Regex를 사용하여 복잡한 문자열을 처리해야 하는 경우가 많아서 작성하게 되었습니다.
JavaScript의 정규식(Regular Expression)에서 이름지정 구문은 정규식 패턴 내에서 캡처 그룹에 이름을 지정하는 기능을 말합니다.
이를 통해 캡처 그룹의 결과를 더 읽기 쉽고 명확하게 할 수 있습니다.

일반적인 정규식 캡처 그룹은 괄호 ()를 사용하여 정의됩니다. 하지만 이름지정 구문을 사용하면 다음과 같은 형식으로 캡처 그룹을 이름지정할 수 있습니다:

```
(?<name>pattern)
```

여기서 <name>은 캡처 그룹에 부여할 이름이고, pattern은 해당 캡처 그룹을 위한 정규식 패턴입니다.

예를 들어, 이름이 있는 캡처 그룹을 사용하여 이메일 주소에서 사용자 이름과 도메인 이름을 추출하는 정규식을 만들어보겠습니다.

```js
const emailRegex =
	/(?<username>[a-zA-Z0-9._%+-]+)@(?<domain>[a-zA-Z0-9.-]+\.[a-zA-Z]{2,})/;

const email = "john.doe@example.com";
const match = email.match(emailRegex);

if (match) {
	const username = match.groups.username;
	const domain = match.groups.domain;
	console.log("Username:", username);
	console.log("Domain:", domain);
}
```

위의 정규식 (?<username>[a-zA-Z0-9._%+-]+)@(?<domain>[a-zA-Z0-9.-]+\.[a-zA-Z]{2,})은 이메일 주소에서 사용자 이름과 도메인 이름을 추출하기 위해 두 개의 이름이 있는 캡처 그룹을 사용합니다. 결과는 다음과 같이 출력됩니다:

```
Username: john.doe
Domain: example.com
```

이름지정 구문을 사용하면 match.groups 객체를 통해 각 캡처 그룹에 쉽게 접근할 수 있어 코드를 읽고 이해하기가 더 쉽고 간결해집니다. 또한 결과 객체에 명시적인 속성 이름으로 접근할 수 있어 가독성을 향상시키는 데 도움이 됩니다.
