# Bash Alias 설정하기

- nginx error / access log 보기
```shell
$ echo "alias nel = 'sudo tail -f /var/log/nginx/error.log'" >> ~/.bash_profile
$ echo "alias nal = 'sudo tail -f /var/log/nginx/access.log'" >> ~/.bash_profile
```