# Bash Alias 설정하기

- terminal 을 사용하다보면 자주 사용하는 명령어들을 alias 해보자.

--- 
## 사용중인 쉘 확인

[사용중인_쉘_보기][OS/Linux/TerminalUsingShell.md] 

## ~/.bash_profile에 alias 추가 



- nginx error / access log 보기
```shell
$ echo "alias nel = 'sudo tail -f /var/log/nginx/error.log'" >> ~/.bash_profile
$ echo "alias nal = 'sudo tail -f /var/log/nginx/access.log'" >> ~/.bash_profile
```