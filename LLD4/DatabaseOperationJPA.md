Java Persistence API (JPA) is a specification for object-relational mapping in Java. It allows you to map your domain objects to relational database tables and vice versa.

Here are some common database operations in JPA:

1. **Creating an Entity:** Entities are plain old Java objects (POJOs) that are mapped to database tables. You create an entity by defining a class and annotating it with `@Entity`.

```java
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private Long id;

    private String name;
    private String email;
    // getters and setters
}
```

2. **Persisting an Entity:** You can save an entity to the database using the `persist` method of the `EntityManager`.

```java
User user = new User();
user.setName("John Doe");
user.setEmail("john.doe@example.com");

EntityManager em = ... // obtain an EntityManager
em.persist(user);
```

3. **Finding an Entity:** You can retrieve an entity from the database using the `find` method of the `EntityManager`.

```java
Long userId = ... // the ID of the user to find
User user = em.find(User.class, userId);
```

4. **Updating an Entity:** You can update an entity by changing its state within a transaction. JPA will automatically synchronize the changes with the database at the end of the transaction.

```java
em.getTransaction().begin();
User user = em.find(User.class, userId);
user.setName("Jane Doe");
em.getTransaction().commit();
```

5. **Deleting an Entity:** You can remove an entity from the database using the `remove` method of the `EntityManager`.

```java
em.getTransaction().begin();
User user = em.find(User.class, userId);
em.remove(user);
em.getTransaction().commit();
```

6. **Querying Entities:** JPA supports JPQL (Java Persistence Query Language), a SQL-like language for querying entities. You can create and execute queries using the `createQuery` method of the `EntityManager`.

```java
Query query = em.createQuery("SELECT u FROM User u WHERE u.email LIKE :email");
query.setParameter("email", "%@example.com");
List<User> users = query.getResultList();
```

Remember that all these operations must be performed within a transaction context (except for queries), which you can start and commit (or rollback) using the `begin`, `commit`, and `rollback` methods of the `EntityTransaction` object obtained from the `EntityManager`.