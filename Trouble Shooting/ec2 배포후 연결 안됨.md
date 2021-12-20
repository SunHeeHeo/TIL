문제 :
<img width="451" alt="KakaoTalk_Photo_2021-12-20-03-18-21" src="https://user-images.githubusercontent.com/88166362/146686204-8c66342e-8313-41ec-bb16-f96e58542d3a.png">

원인 : 배포시 sharp 모듈 문제로, ubuntu에서 node version을 12이상 설치 해줘야 했다
실수는,  혹시 몰라 버전을 조금 업 해서 14로 설치를 해줬다.
원래 배포시 나지 않던 오류가 발생했다.
버전을 내려서 12로 깔아주니, 문제가 말끔히 해결 되었다.

