# zlib란.

![image](https://user-images.githubusercontent.com/77886826/256318488-78f30e05-6e41-4be7-b678-b3c8ae9c9f37.png)

zlib은 Node.js에서 제공하는 압축 및 해제 모듈입니다. 이 모듈을 사용하면 데이터를 압축하거나 압축 해제할 수 있으며, 데이터 크기를 줄이는데 사용됩니다. 주로 파일 압축, 네트워크 통신에서 데이터 압축, 데이터베이스 압축 등 다양한 용도로 사용됩니다.

Node.js의 zlib 모듈은 Gzip, Deflate, Zlib, Brotli 등의 압축 알고리즘을 지원합니다. 이 중에서 가장 일반적으로 사용되는 압축 방식은 Gzip과 Deflate입니다.

Gzip은 파일이나 데이터를 압축할 때 주로 사용되며, Deflate는 데이터를 압축할 때 사용됩니다. Gzip은 Deflate를 기반으로 하며, Deflate에 비해 더 효율적인 압축을 제공합니다.

zlib 모듈은 다음과 같은 메서드를 제공합니다:

zlib.deflateSync(): 데이터를 압축하는 메서드로, 압축된 데이터를 반환합니다.

zlib.inflateSync(): 압축된 데이터를 해제하는 메서드로, 원본 데이터를 반환합니다.

압축과 해제는 다양한 용도로 사용되며, 특히 데이터 전송 및 저장 시 크기를 줄이는데 도움이 됩니다. Node.js의 zlib 모듈을 사용하여 효율적인 데이터 압축과 해제를 수행할 수 있습니다.

## 데이터 압축 예시:

```js
const zlib = require("zlib");

const originalData =
	"Hello, this is some sample data to compress using zlib module.";
const compressedData = zlib.deflateSync(originalData);

console.log("Original Data:", originalData);
//Original Data: Hello, this is some sample data to compress using zlib module.
console.log("Compressed Data:", compressedData.toString("base64"));

//Compressed Data: eJwNwtENgDAIBcBV3gDGOVwDLa...
```

위 예시에서는 zlib.deflateSync() 메서드를 사용하여 originalData를 압축합니다. 압축된 데이터는 버퍼 형태로 반환되며, 필요에 따라 base64 또는 다른 인코딩 방식으로 변환하여 사용할 수 있습니다.

## 데이터 해제 예시:

```js
const zlib = require("zlib");

const compressedData = Buffer.from(
	"eJxLyUjOzytJ1jPL8pM0MzlXyCzJz0wqyUzOLS7JzM8tKcrMLM1OLi5Ozi/JLdQz8xNBAAVJ0Gw==",
	"base64"
);
const decompressedData = zlib.inflateSync(compressedData).toString();

console.log("Compressed Data:", compressedData.toString("base64"));
console.log("Decompressed Data:", decompressedData);
// Decompressed Data: Hello, this is some sample data to compress using zlib module
```

위 예시에서는 zlib.inflateSync() 메서드를 사용하여 압축된 데이터 compressedData를 해제합니다. 해제된 데이터는 원본 데이터인 originalData와 동일한 내용을 가지고 있습니다.

이와 같이 zlib 모듈을 사용하여 데이터 압축 및 해제를 간단하게 수행할 수 있습니다. 데이터 압축은 네트워크 통신이나 데이터 저장 시 데이터 용량을 최적화하여 전송 및 저장 공간을 절약하는데 유용하게 사용됩니다.
