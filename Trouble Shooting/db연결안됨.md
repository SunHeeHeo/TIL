# 씨퀄라이즈 세팅 후, db 연결 안됨.

씨퀄라이즈를 세팅 한후, 
connect econnrefused 127.0.0.1:3306 자꾸 이 에러를 뱉었다.

db 연결이 안되있다고 해서,
다시 설치하고, 비밀번호를 세팅 해주었다.
그러니,
access denided for user 
이라는 에러가 떠서

구글 검색 해보니, root 계정에 접속 권한이 없어서 일어나는 문제라 해서

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '비밀번호'
FLUSH PRIVILEGES;

로 권한을 열어주니 해결 되었다.

[참고 블로그](https://wakestand.tistory.com/495)
