# SpringBoot 실행 시 DataSource 없이 실행하기.

- 현재 버전 : Spring Boot 2.1.7.RELEASE
- 현재  Spring-Data-JPA Dependency 받은 상황.
- 여러가지로 설정할 수 있지만. 저는 Application.java(메인클레스) 에서 Annotation으로 설정하는 방법으로 진행하겠습니다.

```java
@SpringBootApplication(exclude = {DataSourceAutoConfiguration.class, HibernateJpaAutoConfiguration.class, SecurityAutoConfiguration.class})
public class Application {

	public static void main(String[] args) {
		SpringApplication.run(FarmApplication.class, args);
	}

}
```

- SecurityAutoConfiguration.class 같은 경우는 SpringSecurity를 Dependency 받은 상태.
WebSecurityConfig 에 url 별로 경로를 열어주지 않으면 모든 url이 닫혀버리기 때문에 우선적으로 개발 시 해당 Bean을 실행시키지 않도록 추가해준다.

참조자료 : 내 경험