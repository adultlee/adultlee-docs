# 자바스크립트에서 Enum을 구현해보자

Enum은 **Enumerated type** 이라고 하며, 열거하는 타입이라는 의미를 가집니다.

그렇다면 열거하는 타입이라는 것은 어떤 의미를 가질까요?

상수 값 중에 비슷한 종류들을 묶어두기 위해서 자주 사용됩니다.

대표적으로 Enum을 사용하는 언어로는 파이썬이 있습니다.

```py
from enum import Enum

class Colors(Enum):
    RED = 1
    GREEN = 2
    BLUE = 3
```

Python에서는 enum 모듈을 사용하여 열거형(enum)을 정의할 수 있습니다. 열거형은 특정 값을 갖는 고유한 식별자로 구성된 집합을 나타냅니다. 이를 통해 코드를 읽기 쉽고 유지 관리하기 쉽게 만들어줍니다.

다음은 Python에서 enum을 사용하여 열거형을 정의하는 예시입니다

## 하지만 JS에서는...

JavaScript에는 고유한 enum 데이터 유형이 없습니다. 그러나 일반적으로 JavaScript에서는 객체 또는 상수 그룹으로 열거형을 모방하는 방법이 있습니다.

```js
const Colors = {
	RED: "RED",
	GREEN: "GREEN",
	BLUE: "BLUE",
};
console.log(Colors.RED); // 'RED'
console.log(Colors.GREEN); // 'GREEN'
console.log(Colors.BLUE); // 'BLUE'
```

하지만 이경우 부족한 점이 있습니다.

> 단점은 객체 속성의 값을 변경할 수 있다는 것입니다. 따라서 의도적으로 변경하지 않도록 주의해야 합니다.

그래서 다음과 같은 방법으로 극복할 수 있습니다.

```js
const Colors = Object.freeze({
	RED: "RED",
	GREEN: "GREEN",
	BLUE: "BLUE",
});
```

Object.freeze는 객체를 말그대로 얼린다는 뜻입니다.
자세한 문법적인 사항은 [Object.freeze() 문법 공식문서](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze)
에서 찾아 볼 수 있습니다.

다음과 같이 사용하게 되면, 객체의 내부 프로퍼티는 절대 변경되지 않습니다.
