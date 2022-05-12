# EC2 (Amazon Linux 2) 에 Docker 설치

## 1. 인스턴스에 설치한 패키지 및 패키지 캐시 업데이트
```shell
$ sudo yum update -y
```

## 2. 최신 Docker Engine 패키지를 설치
```shell
$ sudo amazon-linux-extras install docker
```

## 3. Docker 서비스 시작
```shell
$ sudo service docker start
```

## (선택사항) 시스템이 재부팅될 때마다 Docker 데몬이 시작되도록 하기
```shell
$ sudo systemctl enable docker
```

## 4. sudo 없이 docker 명령어 실행할 수 있는지 확인
```shell
$ docker info 
```

---
출처 : https://docs.aws.amazon.com/ko_kr/AmazonECS/latest/developerguide/create-container-image.html