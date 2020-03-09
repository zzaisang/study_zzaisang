# SpringBatch Quartz Expression

- 현재 버전 : Spring Boot 2.1.7.RELEASE
- 스프링 배치를 사용하다보면 *.yml에 스케줄러 실행시간을 Quartz 문법으로 작성을 할때가 있다.

#### ForMat

| 필드 명 | 필수여부 | 허용 값 | 허용 특수문자 |
|---|:---:|:---:|---:|
| 초 | 필수 | 0~59 | , - * / |
| 분 | 필수 | 0~59 | , - * / |
| 시 | 필수 | 0~23 | , - * / |
| 일 | 필수 | 1~31 | , - * ? / L W |
| 월 | 필수 | 1~12 OR JAN-DEC | , - * / |
| 주 중 일 | 필수 | 1~7 OR SUN~SAT | , - * ? / L # |
| 년 | 필수 아님 | empty, 1992~1999 | 	, - * / |

##### 특수문자 

| 특수문자 | 의미 |
|:---:|:---:|
|* | 모든 값을 의미합니다. 만약 초에 사용하면 0초~59초까지를 의미합니다.|
|? | 특정 값을 정하지 않은 것입니다. 일과 요일에서 사용가능한데 일에 사용할 경우 어떤 요일도 상관 없는 것 입니다.|
|- | 범위를 의미합니다. 예를 들어 0-10이면 0부터 10까지입니다. 여기서 주의할 것은 마지막 값인 10이 포함된다는 것입니다.|
|, | 값을 추가할 때 사용합니다. 0-10,20-30은 0부터 10까지, 그리고 20부터 30까지를 의미합니다.|
|/ | 증분을 의미합니다. 예를 들어 초에 0/15를 사용하면 15초마다(0, 15, 30, 45) triggering합니다.|
|L | 마지막을 뜻합니다. 날짜에 사용하면 월의 마지막 날을 의미합니다. 31, 30 또는 28(윤달에는 29)일입니다.|
|W | 주중(weekday)를 의미합니다. 날짜와 같이 쓰면 그 날짜가 주중인 날을 의미합니다.| 
|# | n번째를 의미합니다. 그 달의 몇번째 무슨 요일을 설정할 때 사용합니다. 예를 들어 3번째 월요일은 "2#3"으로 설정합니다.|

##### Example

| 표현식 | 뜻 |
|:---:|:---:|
| 0 0 12 * * ? | 매일 12시(정오)|
|0 15 10 ? * * | 매일 오전 10시 15분|
|0 15 10 * * ? | 매일 오전 10시 15분|
|0 15 10 * * ? * | 매일 오전 10시 15분|
|0 15 10 * * ? 2005 | 2005년에 매일 아침 10시 15분|
|0 * 14 * * ? | 매일 오후 2시 0분 ~ 59분|
|0 0/5 14 * * ? | 매일 오후 2시부터 2시 55분까지 5분마다|
|0 0/5 14,18 * * ? | 매일 오후 2시부터 2시 55분까지 5분마다, 6시부터 6시 55분까지 5분마다|
|0 0-5 14 * * ? | 매일 오후 2시부터 2시 5분까지 매분|
|0 10,44 14 ? 3 WED | 매년 3월의 수요일마다 오후 2시 10분과 2시 44분|
|0 15 10 ? * MON-FRI | 월요일부터 금요일까지 오전 10시 15분|
|0 15 10 15 * ? | 매달 15일 오전 10시 15분|
|0 15 10 L * ? | 매달 마지막 날 오전 10시 15분|
|0 15 10 ? * 6L | 매달 마지막 금요일 오전 10시 15분|
|0 15 10 ? * 6L 2002-2005 | 2002년부터 2005년까지 매달 마지막 금요일 오전 10시 15분|
|0 15 10 ? * 6#3 | 매달 3번째 금요일 오전 10시 15분|
|0 0 12 1/5 * ? | 매달 첫날부터 5일마다 12시(정오)|
|0 11 11 11 11 ? | 매년 11월 11일 오전 11시 11분|

참조자료 : <http://www.quartz-scheduler.org/documentation/quartz-2.3.0/tutorials/crontrigger.html>