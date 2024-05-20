API versioning can be achieved in several ways in Java, especially when using frameworks like Spring Boot. Here are a few common strategies:

1. **URI Versioning**: This is the most straightforward approach where the API version is included directly in the URI.

```java
@RequestMapping("api/v1/users")
public class UserControllerV1 { /*...*/ }

@RequestMapping("api/v2/users")
public class UserControllerV2 { /*...*/ }
```

2. **Request Parameter Versioning**: In this approach, the version is passed as a request parameter.

```java
@RequestMapping(value = "api/users", params = "version=1")
public class UserControllerV1 { /*...*/ }

@RequestMapping(value = "api/users", params = "version=2")
public class UserControllerV2 { /*...*/ }
```

3. **Header Versioning**: Here, the version is included in a custom header.

```java
@RequestMapping(value = "api/users", headers = "X-API-VERSION=1")
public class UserControllerV1 { /*...*/ }

@RequestMapping(value = "api/users", headers = "X-API-VERSION=2")
public class UserControllerV2 { /*...*/ }
```

4. **Media Type Versioning (a.k.a “content negotiation” or “accept header”)**: The version is included in the Accept header in the request.

```java
@RequestMapping(value = "api/users", produces = "application/vnd.company.app-v1+json")
public class UserControllerV1 { /*...*/ }

@RequestMapping(value = "api/users", produces = "application/vnd.company.app-v2+json")
public class UserControllerV2 { /*...*/ }
```

Each of these methods has its own pros and cons, and the choice between them depends on your specific use case.

If you're changing how clients authenticate with or are authorized by your API, you'll need to version your API to ensure existing clients can still authenticate and are authorized correctly. Here's an example of how you might implement this in a Spring Boot application using header versioning:

```java
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping(value = "/api/users", headers = "X-API-VERSION=1")
public class UserControllerV1 {

    @GetMapping
    public String getUsersV1() {
        // Authentication and authorization logic for version 1
        return "User details from API version 1";
    }
}

@RestController
@RequestMapping(value = "/api/users", headers = "X-API-VERSION=2")
public class UserControllerV2 {

    @GetMapping
    public String getUsersV2() {
        // New authentication and authorization logic for version 2
        return "User details from API version 2";
    }
}
```

In this example, `UserControllerV1` and `UserControllerV2` are two versions of the same controller. They both handle requests to `/api/users`, but the version of the API is determined by the `X-API-VERSION` header in the request.

`UserControllerV1` uses the original authentication and authorization logic, while `UserControllerV2` uses the new logic. This way, clients that are still using version 1 of the API can continue to authenticate and be authorized correctly, while clients that are ready to use version 2 can take advantage of the new authentication and authorization features.