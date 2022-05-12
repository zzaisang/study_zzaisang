# EC2 에 docker-compose 설치


## 1. docker-compose latest (최신) 버전 설치
```shell
$ sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
```

## 2. docker-compose 명령어 실행 권한 부여
```shell
$ sudo chmod +x /usr/local/bin/docker-compose
```

---
출처 : https://github.com/docker/compose