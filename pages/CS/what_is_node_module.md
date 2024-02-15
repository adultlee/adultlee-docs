# node_Modules란?

node_modules는 Node.js 프로젝트에서 사용되는 외부 라이브러리와 모듈을 저장하는 디렉토리입니다. Node.js는 모듈 시스템을 통해 코드를 모듈화하고, 이 모듈들을 다른 모듈에서 불러와 사용할 수 있게 해줍니다. 이 때, 프로젝트가 의존하는 외부 라이브러리와 모듈들은 node_modules 디렉토리에 저장되며, 이를 관리하는 도구로는 주로 npm (Node Package Manager)이나 Yarn 등이 사용됩니다.

node_modules 디렉토리는 보통 프로젝트의 루트 디렉토리에 위치하며, 프로젝트가 의존하는 라이브러리들이 하위 디렉토리로 설치됩니다. 이러한 디렉토리 구조는 다른 프로젝트에서도 동일한 패키지 의존성을 관리할 수 있도록 도와줍니다. 각 패키지는 자체적으로 package.json 파일에 패키지 정보와 의존성 정보를 기록하여 관리합니다.

Node.js 애플리케이션을 개발할 때, 자주 사용되는 라이브러리들은 npm이나 yarn과 같은 패키지 매니저를 통해 간편하게 설치할 수 있습니다. 예를 들어, 다른 개발자가 만든 유용한 모듈을 사용하려면 해당 모듈을 설치하여 node_modules 디렉토리에 저장하고, 이후에 애플리케이션 코드에서 해당 모듈을 require 함수를 통해 불러와서 사용할 수 있습니다.

## 여러 package manager

<img width="200" alt="image" src="https://github.com/adultlee/adultlee-docs/assets/77886826/91784f43-a855-4a14-8d9b-45854bc21b66">
<img width="200" alt="image" src="https://github.com/adultlee/adultlee-docs/assets/77886826/770c4593-60f1-4fa1-9783-b7eb9691bec4">
<img width="200" alt="image" src="https://github.com/adultlee/adultlee-docs/assets/77886826/69eced59-67ba-4ef6-93f9-839b2c8f497c">
<img width="200" alt="image" src="https://github.com/adultlee/adultlee-docs/assets/77886826/e8a3540a-b554-4b17-9494-a4a77eb2bbe2">

## 요약

1. node_modules는 Node.js 프로젝트에서 외부 패키지와 모듈을 저장하는 디렉토리
2. 프로젝트의 의존성을 관리하고 다른 모듈을 불러와 사용할 수 있도록 도와주는 역할
3. **_하지만 패키지 매니저의 종류에 따라서 그 구조가 확연히 다릅니다._**
