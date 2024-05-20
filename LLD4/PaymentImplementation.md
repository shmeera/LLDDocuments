Here's a simple example of a payment module implementation in Java. This example uses the Strategy pattern to allow for different types of payment methods (like credit card, PayPal, etc.).

First, define an interface for the payment method:

```java
public interface PaymentMethod {
    void pay(double amount);
}
```

Then, implement this interface for each payment method:

```java
public class CreditCard implements PaymentMethod {
    @Override
    public void pay(double amount) {
        System.out.println("Paid " + amount + " using Credit Card.");
    }
}

public class PayPal implements PaymentMethod {
    @Override
    public void pay(double amount) {
        System.out.println("Paid " + amount + " using PayPal.");
    }
}
```

Next, create a `PaymentService` class that uses a `PaymentMethod`:

```java
public class PaymentService {
    private PaymentMethod paymentMethod;

    public PaymentService(PaymentMethod paymentMethod) {
        this.paymentMethod = paymentMethod;
    }

    public void pay(double amount) {
        paymentMethod.pay(amount);
    }
}
```

Finally, you can use the `PaymentService` with different payment methods:

```java
public class Main {
    public static void main(String[] args) {
        PaymentService paymentService = new PaymentService(new CreditCard());
        paymentService.pay(100.0);

        paymentService = new PaymentService(new PayPal());
        paymentService.pay(200.0);
    }
}
```

This is a very basic example. In a real-world application, you would likely have more complex logic, such as validating the payment information, handling payment errors, and so on.