# crypto에 대해서

crypto는 Node.js의 내장 모듈 중 하나로, 다양한 암호화 기능을 제공하는 모듈입니다. 이 모듈을 사용하여 해시 함수, 암호화, 복호화, 서명 등 다양한 보안 관련 작업을 수행할 수 있습니다.

주요 기능과 사용 예시는 다음과 같습니다:

해시 함수 사용 예시:
해시 함수는 주어진 데이터를 고정된 길이의 문자열로 변환하는 함수로, 데이터의 무결성을 검증하는데 사용됩니다.

```js
const crypto = require("crypto");

const dataToHash = "Hello, this is some data to hash."; // 바꿀 정보
const hash = crypto.createHash("sha256").update(dataToHash).digest("hex");

console.log("Original Data:", dataToHash);
// Original Data: Hello, this is some data to hash.
console.log("Hash:", hash);
// Hash: aec5e9f3cef7405d068029e473e2199aae1f99c3db4593b3a24d5026b4735665
```

암호화 및 복호화 사용 예시:
암호화와 복호화는 데이터를 암호화하여 안전하게 저장하거나 전송한 후 필요 시 다시 원래의 데이터로 변환하는 작업입니다.

```js
const crypto = require("crypto");

const secretKey = "mySecretKey";
const dataToEncrypt = "Hello, this is some data to encrypt.";

// 암호화
const cipher = crypto.createCipher("aes-256-cbc", secretKey);
let encryptedData = cipher.update(dataToEncrypt, "utf8", "hex");
encryptedData += cipher.final("hex");

// 복호화
const decipher = crypto.createDecipher("aes-256-cbc", secretKey);
let decryptedData = decipher.update(encryptedData, "hex", "utf8");
decryptedData += decipher.final("utf8");

console.log("Original Data:", dataToEncrypt);
//Original Data: Hello, this is some data to encrypt.
console.log("Encrypted Data:", encryptedData);
//Encrypted Data:6ba7a41fef0c7e4744bf..........
console.log("Decrypted Data:", decryptedData);
//Decrypted Data: Hello, this is some data to encrypt.
```

서명 및 검증 사용 예시:
서명은 데이터의 무결성과 인증을 보장하기 위해 사용됩니다. 데이터에 서명을 생성하여 해당 데이터를 생성한 사람(또는 시스템)을 인증하고, 데이터의 무결성이 보장되었는지 확인할 수 있습니다.

```js
const crypto = require("crypto");

const privateKey = crypto.generateKeyPairSync("rsa", {
	modulusLength: 2048,
	privateKeyEncoding: {
		type: "pkcs1",
		format: "pem",
	},
	publicKeyEncoding: {
		type: "spki",
		format: "pem",
	},
});

const dataToSign = "Hello, this is some data to sign.";

// 서명 생성
const sign = crypto.createSign("RSA-SHA256");
sign.update(dataToSign);
const signature = sign.sign(privateKey.privateKey, "hex");

// 서명 검증
const publicKey = privateKey.publicKey;
const verify = crypto.createVerify("RSA-SHA256");
verify.update(dataToSign);
const isSignatureValid = verify.verify(publicKey, signature, "hex");

console.log("Original Data:", dataToSign);
//Original Data: Hello, this is some data to sign.
console.log("Signature:", signature);
//Signature: 4ac7aea23265ea1.........
console.log("Signature is Valid:", isSignatureValid);
// Signature is Valid: true
```

이렇게 crypto 모듈을 사용하여 해시 함수, 암호화, 복호화, 서명 등 보안 관련 작업을 간단히 수행할 수 있습니다. 이 모듈을 적절히 활용하여 데이터 보안을 강화할 수 있습니다.
