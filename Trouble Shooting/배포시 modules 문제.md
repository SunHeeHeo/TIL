# 배포시 modules 문제 발생의 원인이었던 실수 정리 

<img width="1119" alt="스크린샷 2021-12-15 오전 1 21 04" src="https://user-images.githubusercontent.com/88166362/146050348-d2b9407d-8554-4204-a194-cee50da252b2.png">

1. node version을 최소 12 이상 설치 할 것 
참고 코드
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash

-----------------

nvm install v14.17.6
```

2. npm i 는 root가 아닌 ubuntu에서 할 것(혹여나 이런 실수를 할수 있으니까!)

3. 발표전날 서버가 터진건, cpu 용량을 넘어서 였다. 이번 새 서버에 배포할때 똑같은 일이 일어 났는데, ec2에 네트워크를 체크 해보니 이렇게 cup 용량이 가득 찼었다.
그래서 ec2를 업그레이드 해주니, 문제가 해결 되었다!


