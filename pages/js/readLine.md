# ReadLine 이란?

JavaScript의 readline은 Node.js 환경에서 사용되는 모듈 중 하나입니다. 이 모듈은 터미널에서 사용자로부터의 입력을 받을 수 있게 해주는 기능을 제공합니다. readline 모듈을 사용하면 스트림(stream)에서 데이터를 읽어오고, 터미널에서 사용자로부터의 입력을 처리할 수 있습니다.

readline 모듈을 사용하기 위해서는 Node.js의 기본 모듈 중 하나인 fs 모듈을 require로 불러와야 합니다.

```js
const readline = require("readline");
```

readline 모듈은 createInterface 메서드를 사용하여 인터페이스를 생성합니다. 이 인터페이스는 input과 output으로 스트림을 설정하고, line 이벤트를 통해 입력된 각 줄에 대한 이벤트 핸들러를 등록합니다. 예를 들면 다음과 같습니다

```js
const rl = readline.createInterface({
	input: process.stdin,
	output: process.stdout,
});
// line은 한줄 입력 받을 때마다, 두번째 인자의 함수를 실행시킨다는 의미입니다.
rl.on("line", (input) => {
	console.log(`입력된 값: ${input}`);
});
```

위의 예제에서는 process.stdin으로 입력 스트림을 설정하고, process.stdout로 출력 스트림을 설정했습니다. rl 객체의 on 메서드를 사용하여 line 이벤트를 등록하고, 입력된 각 줄에 대해 이벤트 핸들러를 실행하도록 했습니다. 이벤트 핸들러에서는 입력된 값을 출력하는 단순한 예제입니다.

readline 모듈을 사용하여 사용자로부터 여러 줄의 입력을 받을 수도 있고, 특정 조건에 따라 입력을 처리하거나 반복적으로 입력을 받을 수도 있습니다. readline의 다양한 메서드를 사용하여 입력 처리를 유연하게 구성할 수 있습니다.

### 주의할 점

| readline은 Node.js 환경에서 동작하는 모듈이므로 브라우저에서는 사용할 수 없다는 점입니다.

## 입력을 종료한 후 여러번 실행시키는 방법

```js
const readline = require("readline");

const rl = readline.createInterface({
	input: process.stdin,
	output: process.stdout,
});

let sum = 0;

function addNumbers() {
	rl.question('숫자를 입력하세요 (종료하려면 "q"를 입력하세요): ', (input) => {
		if (input.toLowerCase() === "q") {
			console.log(`총합: ${sum}`);
			rl.close();
		} else {
			const number = parseInt(input);
			if (!isNaN(number)) {
				sum += number;
				console.log(`현재 총합: ${sum}`);
			} else {
				console.log("유효한 숫자를 입력하세요.");
			}
			addNumbers();
		}
	});
}

addNumbers();
```

## 한번에 여러줄 입력을 처리하는 방법

```js
const readline = require("readline");

const rl = readline.createInterface({
	input: stdin,
	output: stdout,
});

const input = [];

rl.on("line", (line) => {
	input.push(line);
	rl.close();
}).on("close", () => {
	console.log(input);
	process.exit();
});
```
