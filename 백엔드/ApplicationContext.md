##### : 빈(Bean) 을 생성하고 관리 
= ==스프링 컨테이너==

- 인터페이스임
+ 구현체 : `AnnotationConfigApplicationContext`
+ [[BeanRactory]] (interface) 를 상속받아 기능을 제공한다. 
+ 빈의 관리, 조회 이외의 부가기능이 있다. 
	+ 메시지 소스를 활용한 **국제화 기능** (ex. 한국에서는 한국어로, 영어권에서는 영어로 출력)
	+ **환경변수** - 로컬, 개발, 운영 등을 구분해서 처리 (EnvironmentCapable)
	+ **애플리케이션 이벤트** (ApplicationEventPublisher)
	+ 편리한 **리소스 조회** (ResourceLoader)

### 1. 스프링 컨테이너 생성 
+ `new AnnotaionConfigApplicationContext(AppConfig.class)`
+ 스프링 컨테이너를 생성할 때는 구성 정보를 지정해주어야 함. 
	+ **AppConfig.class** 를 파라미터로 넘김 
![[스프링 컨테이너 생성.png]]
### 2. 스프링 빈 등록 
+ `@Bean` 이 붙은 모든 메소드를 스프링 빈에 등록한다. 
	+ 빈 이름은 보통 메소드 명으로 통일. 같은 이름이 있으면 안됨! 

![[스프링 빈 등록.png]]
### 3. 스프링 빈 의존관계 설정- 빈 생성
![[스프링 빈 의존관계 설정 - 빈 생성.png]]
### 4. 스프링 빈 의존관계 설정 - 의존관계 주입
![[스프링 빈 의존관계 설정 - 의존관계 주입.png]]

``` java
AnnotationConfigApplicationContext ac = new AnnotationConfigApplicationContext(AppConfig.class); 

String[] beans = ac.getBeanDefinitionNames(); // 스프링에 등록된 모든 빈 이름 조회 
Object bean = ac.getBean(); // 빈 이름으로 객체(인스턴스)를 조회 : 타입으로 조회  
Map<String, 빈 타입> beans = ac.getBeansOfType(빈 클래스 타입); // 특정 타입 모두 조회
// 부모 타입으로 조회하면, 자식 타입도 같이 조회 됨. 
// 즉, Object로 조회하면 모든 스프링 빈 조회 

if(beanDefinition.getRole() == BeanDefinition.ROLE_APPLICATION) { 
	// getRole()로 스프링이 내부에서 사용하는 빈을 구분할 수 있다. 
	// ROLE_APPLICATION : 일반적으로 사용자가 정의한 빈 
	// ROLE_INFRASTRUCTURE : 스프링이 내부에서 사용하는 빈 
	Object bean = ac.getBean(beanDefinitionName);  
}
```

