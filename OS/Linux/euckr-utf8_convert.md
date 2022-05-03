# csv 파일 UTF-8, EUC-KR 문서 변환

csv 파일 내 인코딩 방식이 euc-kr 로 지정되어 있어서 파일 읽을때 문제가 있었다.
간단한 명령어로 해결

## iconv
```shell
#hello.csv 파일 utf-8 에서 euc-kr 로 변환
$ iconv -c -f utf-8 -t euc-kr hello.csv > hello_euc.csv

#hello.csv 파일 euc-kr 에서 utf-8 로 변환
$ iconv -c -f euc-kr -t utf-8 hello.csv > hello_euc.csv 
```


---
출처 :https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=ambidext&logNo=221223387207