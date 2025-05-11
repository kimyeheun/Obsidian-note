#### Constructor Injection
```java
public class UserService {
    private UserRepository userRepository;

    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```
#### Setter Injection
```java
public class OrderService {
    private PaymentGateway paymentGateway;

    @Autowired
    public void setPaymentGateway(PaymentGateway paymentGateway) {
        this.paymentGateway = paymentGateway;
    }
}
```
#### Field Injection
```java
@Service
public class ProductService {
    @Autowired
    private ProductRepository productRepository;
    
    // ...
}
```
#### Method Injection
```java
@Component
public class ReportGenerator {
    private EmailService emailService;

    @Autowired
    public void setEmailService(EmailService emailService) {
        this.emailService = emailService;
    }
    
    public void generateReport() {
        // Use the emailService here...
    }
}
```
#### Configuration
```java
@Configuration
public class AppConfig {
    @Bean
    public UserService userService(UserRepository userRepository) {
        return new UserService(userRepository);
    }
    
    @Bean
    public UserRepository userRepository() {
        return new UserRepository();
    }
```