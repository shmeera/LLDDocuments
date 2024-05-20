To enable debugging log in a Spring Boot application, you need to set the logging level to `DEBUG` in your application properties file. 

You can do this in the `application.properties` file:

```properties
logging.level.root=DEBUG
```

Or in the `application.yml` file:

```yaml
logging:
  level:
    root: DEBUG
```

These configurations set the logging level to `DEBUG` for all loggers in your application. If you want to enable debug logging for a specific package or class, you can replace `root` with the package or class name. For example, to enable debug logging for all classes in the `com.example` package, you can use:

```properties
logging.level.com.example=DEBUG
```

After you've made these changes, restart your application. You should now see debug logs in your console or log file.
## What is dependency Injection?
The process of injecting dependent bean objects into target bean objects is called dependency injection.

Setter Injection: The IOC container will inject the dependent bean object into the target bean object by calling the setter method.
Constructor Injection: The IOC container will inject the dependent bean object into the target bean object by calling the target bean constructor.
Field Injection: The IOC container will inject the dependent bean object into the target bean object by Reflection API.

## IoC Container is a framework for implementing automatic dependency injection. It manages object creation and its life-time and also injects dependencies into the class.

## What does the @SpringBootApplication annotation do internally?
The @SpringBootApplication annotation is equivalent to using @Configuration, @EnableAutoConfiguration, and @ComponentScan with their default attributes. Spring Boot enables the developer to use a single annotation instead of using multiple. But, as we know, Spring provided loosely coupled features that we can use for each annotation as per our project needs.

## How does a spring boot application get started?
Just like any other Java program, a Spring Boot application must have a main method. This method serves as an entry point, which invokes the SpringApplication#run method to bootstrap the application.

@SpringBootApplication 
public class MyApplication { 
   
       public static void main(String[] args) {    
    
             SpringApplication.run(MyApplication.class);        
               // other statements     
       } 
}