# nodejs에서의 비동기 이벤트를 수행하는 libuv.

[Libuv git repo](https://github.com/libuv/libuv)

## Libuv 란

libuv는 Node.js에서 사용되는 C 라이브러리로, 비동기 I/O 작업을 처리하고 멀티플랫폼 환경에서 일관된 API를 제공하는 역할을 합니다. Node.js는 주로 이 라이브러리를 통해 비동기적인 I/O 작업을 처리하며, 이를 통해 Node.js가 뛰어난 확장성과 성능을 가질 수 있게 됩니다.

![](https://velog.velcdn.com/images/adultlee/post/8c30478f-2db3-452b-9413-94b73952ae81/image.png)

위의 사진은 **_빨간색 소년_**님의 NodeJs 생태계에 대한 아키텍쳐 입니다.
너무 좋은 설명이라 참고하였으며, 해당 글 또한 해당 글을 참고하여 작성되었습니다.

### 1. event loop

이벤트 루프는 가능하다면 언제나 시스템 커널에 작업을 떠넘겨서 Node.js가 논 블로킹 I/O 작업을 수행하도록 해줍니다.(JavaScript가 싱글 스레드임에도 불구하고)

대부분의 현대 커널은 멀티 스레드이므로 백그라운드에서 다수의 작업을 실행할 수 있습니다. 이러한 작업 중 하나가 완료되면 커널이 Node.js에게 알려주어 적절한 콜백을 poll 큐에 추가할 수 있게 하여 결국 실행되게 합니다. 이 부분에 대한 자세한 설명은 다른 글에서 설명하겠습니다.

각각의 phaze에 대해서는 아주 중요하지만 다른 부분에서 처리하도록 하겠습니다.

### 2. thread

libuv에는 워커 쓰레드풀(default 4개)이 생성됩니다.

node.js는 single thread라는 건, event loop가 single thread라는 걸 의미하며 여러개의 thread를 사용한다는 건 libuv thread pool을 의미합니다.

### 3. uv_io

uv_io는 libuv의 I/O 이벤트 처리를 담당하는 부분 중 하나입니다. 이는 주로 파일과 소켓과 같은 I/O 리소스와 관련하여 사용됩니다. libuv에서는 I/O 이벤트를 감지하고 처리하기 위해 uv_io 구조체와 관련된 함수들을 제공합니다.

uv_io->data: 사용자 정의 데이터를 저장하는 포인터입니다. 이 멤버를 활용하여 콜백 함수 내에서 사용자 정의 데이터에 접근할 수 있습니다.

uv_io->fd: 파일 디스크립터를 나타내는 정수 값입니다. 파일 또는 소켓과 같은 I/O 리소스를 식별하기 위해 사용됩니다.

uv_io->events: 감지할 I/O 이벤트를 나타내는 정수 값입니다. 일반적으로 UV_READABLE 또는 UV_WRITABLE과 같은 값으로 설정하여 읽기 또는 쓰기 가능한 상태를 감지할 수 있습니다.

uv_io->cb: I/O 이벤트가 발생했을 때 호출될 콜백 함수를 가리키는 함수 포인터입니다.

I/O 이벤트를 감지하고 처리하기 위해 libuv는 이벤트 루프를 사용하며, uv_io와 같은 구조체와 관련된 함수들은 해당 이벤트 루프를 조작하는 데 사용됩니다. 이렇게 libuv가 I/O 이벤트를 관리하면서 Node.js와 같은 비동기 애플리케이션 개발에 도움을 줍니다.

# Reference

### [완벽한 NodeJs blog](https://sjh836.tistory.com/149)

### [Node js 공식문서 중 event loop](https://nodejs.org/ko/docs/guides/event-loop-timers-and-nexttick)
