# Maria DB Local 세팅하기

### 환경 
 - MAC OS 

## Maria DB 설치
 - Homebrew 로 설치.
```shell script
brew update 
brew install mariadb 
```
 - 따로 mariadb 버전을 세팅하지 않으면 최신버전이 설치된다.
 - 설치가 완료되면 해당 문구처럼 로깅이 찍힐것이다.
 ```
A "/etc/my.cnf" from another install may interfere with a Homebrew-built
server starting up correctly.

MySQL is configured to only allow connections from localhost by default

To connect:
    mysql -uroot

To have launchd start mariadb now and restart at login:
  brew services start mariadb
Or, if you don't want/need a background service you can just run:
  mysql.server start
==> Summary
🍺  /usr/local/Cellar/mariadb/10.4.11: 742 files, 168MB
==> Caveats
==> mecab-ipadic
To enable mecab-ipadic dictionary, add to /usr/local/etc/mecabrc:
  dicdir = /usr/local/lib/mecab/dic/ipadic
==> mariadb
A "/etc/my.cnf" from another install may interfere with a Homebrew-built
server starting up correctly.

MySQL is configured to only allow connections from localhost by default

To connect:
    mysql -uroot

To have launchd start mariadb now and restart at login:
  brew services start mariadb
Or, if you don't want/need a background service you can just run:
  mysql.server start
```

## 설치 끝 
