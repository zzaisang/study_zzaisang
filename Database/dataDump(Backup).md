# Maria DB 테이블 Dump(백업) 하기

### 덤프 옵션
 - 'u' : 아이디
 - 'p' : 비밀번호
 - '>' : dump output 
 - '<' : dump input   
 - 'data-dump-ysf.sql' : 해당 파일로 input Or output
### 전체 테이블 dump
```mysql
mysqldump -uysf_dev --port=3306 --host=localhost -p1234 ysf_dev > data-dump-ysf.sql
```

### 이벤트 테이블을 제외한 전체 테이블 dump
```mysql
mysqldump -uysf_dev --port=3306 --host=localhost -p1234 ysf_dev --ignore-table=mysql.event > data-dump-ysf.sql
```

### 특정 테이블 dump (test_table) 만 dump
```mysql
mysqldump -uysf_dev --port=3306 --host=localhost -p1234 ysf_dev test_table > data-dump-ysf.sql
```

### dump 데이터 적재(input)
```mysql
mysql -uysf_dev --port=3306 --host=localhost -p1234 ysf_dev < data-dump-ysf.sql
```