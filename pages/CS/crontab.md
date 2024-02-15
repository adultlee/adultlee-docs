# crontab으로 구현하는 자동화 루틴 개요

자동화를 하기 위해선?

1. 자동화를 진행할 코드 작성
2. 자동화를 위한 명령어 (bash)

<img width="464" alt="image" src="https://user-images.githubusercontent.com/77886826/253718575-b25605ba-9963-4e67-9c5f-a700c78ed008.png">

/etc/crontab 을 열어서 다음과 같이 설정을 진행하면 됩니다.

상대 경로로 이동한 뒤, 명령어를 통해서 내가 원하는 기능을 실행시키는 것이 중요합니다.

시간 설정 방법은 간단하게 찾아보면 알 수 있지만 남겨보자면,

<img width="893" alt="image" src="https://user-images.githubusercontent.com/77886826/253719621-7415ec15-a83a-4d53-87c9-5fd8dd1db3c5.png">

```
예시)
  *   *  *   *   *
# 분  시  일  월   주

# 예 : 매일 오후 6시 30분에 크론잡을 등록하는 경우.
30 18 * * * rm /home/adultlee/tmp/*
# 예 : 5분 간격으로 동작하는 크론잡을 등록하는 경우.
*/5 * * * * rm /home/adultlee/tmp/*
# 예 : 매 5시간 간격으로 동작하는 크론잡을 등록하는 경우.
* */5 * * * rm /home/adultlee/tmp/*
```

<img width="536" alt="image" src="https://user-images.githubusercontent.com/77886826/253719337-5eff9a1d-765e-4ea9-833c-1b0c079db37e.png">

15분에 한번씩, /index.js를 실행시켰으며  
1시간에 한번씩, /main.sh 스크립트를 실행시켰습니다.

> OS마다 crontab의 위치가 다릅니다.
