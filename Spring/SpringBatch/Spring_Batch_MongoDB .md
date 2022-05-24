# Spring Batch DataSource 의존 제거하기
## Failed to configure a DataSource: 'url' attribute is not specified and no embedded datasource could be configured. 에러 해결

- Application 실행시 DB 연결하라는 문구가 뜬다.
- 해결방법 : @SpringBootApplication 에 (exclude = DataSourceAutoConfiguration.class) 추가
```java
@SpringBootApplication(exclude = DataSourceAutoConfiguration.class)
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
} 
```