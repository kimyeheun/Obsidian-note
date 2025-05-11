##### : Open/Closed Principle

- ==확장에는 열려있으나, 변경에는 닫혀== 있어야 한다.
- **다형성** 활용. 인터페이스를 구현하는 것은 → 기존의 코드를 변경하는 것이 아님 + 코드 확장

    근데!! 구현 객체를 변경하는 것은 클라이언트 코드를 변경해야 한다는 의미잖아? 
    어라? 다형성 활용했는데? OCP 원칙이 안 지켜진다? 
    why? 인터페이스에 의존하지만, **구현체에도 의존**하기 때문
    == DIP 위반 ⇒ 객체를 생성하고 연관 관계를 맺어주는 *별도의 **조립, 설정자***가 필요하다.
	    * 조립, 설정자 : ex. AppConfig - 여기서 대신 객체를 생성하고 주입해준다(관심사의 분리)*

``` java
public class OrderService {
    private final KakaoPayProcessor kakaoPay = new KakaoPayProcessor(); // ❌
}
```
🔽 `new 생성자()` 를 없애기 위해 아래처럼 변경
``` java
public class OrderService {
    private final PaymentProcessor processor;

    // 생성자 주입 (DI)
    public OrderService(PaymentProcessor processor) {
        this.processor = processor;
    }
}
```