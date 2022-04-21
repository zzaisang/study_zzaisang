# Maria DB 로컬 server 세팅

### Maria DB 설치 방법 
 - [MariaDB_Install](MariaDB_Install.md)
 
----
 - 서버 시작
```shell script
mysql.server start
```
 - mysql 서버 접속 (완료되면 아래 이미지 처럼 나온다.)
```shell script
mysql
```
![서버접속](imgysql_server_start.png)

### root 계정 비밀번호 설정 

```mysql
UPDATE user SET authentication_string=PASSWORD('###') where User='root'; #(###은 비밀번호)
FLUSH PRIVILEGES;
```

### database(schema) 생성 및 유저 생성 후 권한 부여
```mysql
CREATE DATABASE ysf_dev;
CREATE USER 'ysf_dev'@'%'IDENTIFIED BY '1234';
GRANT ALL PRIVILEGES on ysf_dev.* TO 'ysf_dev'@'%';
FLUSH PRIVILEGES;
```