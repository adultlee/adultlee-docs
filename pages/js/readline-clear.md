# readline을 통해서 반복적으로 입력을 받을때, 출력문이 입력창을 침범하는 문제를 해결하는 방법

```js
function clearConsole() {
	process.stdout.write("\x1B[2J\x1B[0f");
}
```

을 내가 원하는 시점에 선언하여 console을 모두 지울 수 잇습니다.

" \x1B[2J\x1B[0f "는 ANSI Escape Code 중 하나로, 콘솔 화면을 지우는 명령입니다. 이를 통해 이전 출력을 지우고 새로운 내용을 출력할 수 있습니다.

구체적으로 각 제어 문자들의 역할은 다음과 같습니다:

```
\x1B: 이스케이프 문자(ESC)
[: 제어 시퀀스의 시작을 나타냄
2J: 화면을 지우는 제어 시퀀스. 콘솔의 내용을 완전히 지웁니다.
\x1B: 이스케이프 문자(ESC)
[: 제어 시퀀스의 시작을 나타냄
0f: 커서를 화면의 시작 위치(1행 1열)로 이동시키는 제어 시퀀스.
```

이렇게 사용하면 콘솔 화면을 완전히 지우고, 커서를 다시 첫 번째 행의 첫 번째 열로 이동시켜서 새로운 출력을 시작할 수 있습니다. 즉, 새로운 내용이 출력되는 위치가 이전 출력의 위치에 덮어씌워지게 됩니다.

참고로, ANSI Escape Code는 다양한 터미널에서 색상, 스타일, 위치 등을 제어하기 위해 사용되는 특수한 문자열입니다. 이 코드들은 터미널에서 동작하며, 모든 터미널에서 지원되지는 않을 수 있습니다. 따라서, 위의 코드가 모든 환경에서 작동하는 것을 보장할 수는 없습니다. 특히, 일부 플랫폼이나 터미널 환경에서는 제대로 동작하지 않을 수 있으니 참고하시기 바랍니다.

따라서,

```js
const readline = require("readline");

const rl = readline.createInterface({
	input: process.stdin,
	output: process.stdout,
});

let sum = 0;
function clearConsole() {
	process.stdout.write("\x1B[2J\x1B[0f");
}

function main() {
	rl.question('숫자를 입력하세요 (종료하려면 "q"를 입력하세요): ', (input) => {
		if (input.toLowerCase() === "q") {
			console.log(`총합: ${sum}`);
			rl.close();
		} else {
			clearConsole();
			const number = parseInt(input);
			if (!isNaN(number)) {
				sum += number;
				console.log(`현재 총합: ${sum}`);
			} else {
				console.log("유효한 숫자를 입력하세요.");
			}
			main();
		}
	});
}
main();
```

다음과 같이 입력하면, 내가 원하는 시점에서 다시 console을 지워 보다 명확하게 출력을 진행할 수 있습니다.
