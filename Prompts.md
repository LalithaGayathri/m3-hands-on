## Part A — First suggestion

public record UserDTO(
    String username,
    String email,
    String firstName,
    String lastName
) {
    public static UserDTO fromUser(User user) {
        return new UserDTO(
            user.getUsername(),
            user.getEmail(),
            user.getFirstName(),
            user.getLastName()
        );
    }
}

## Second suggestion
public record UserDTO(long id, String name, String email, boolean active) {
    public static UserDTO fromUser(User user) {
        return new UserDTO(user.getId(), user.getName(), user.getEmail(), user.isActive());
    }
}

## Part B — Mapper

### Copilot-generated mapper

    public static UserDTO fromUser(User user) {
        return new UserDTO(user.getId(), user.getName(), user.getEmail(), user.isActive());
    }
The generated mapper compiled successfully using Java 17.
No hallucinated field or method was detected.

`Runtime test:`

Created a User with:
id = 1
name = Alice
email = alice@example.com
active = true

The resulting UserDTO was:
UserDTO[id=1, name=Alice, email=alice@example.com, active=true]

## Part C 

### Copilot suggestion for getOrderById
```java
return store.get(id);
```

### Copilot suggestion for createorder

```java
if (item == null || item.isEmpty() || qty <= 0) {
    throw new IllegalArgumentException("Invalid item or quantity");
}
Order newOrder = new Order(nextId++, item, qty);
store.put(newOrder.id(), newOrder);
return newOrder;
```
### Part D:

## copilot generated commit message:
Implement UserDTO and OrderController methods for user and order management

## Edited messsage:

Complete UserDTO and OrderController

Implemented the missing mapper and order methods using Copilot suggestions,
and documented the autocomplete observations in Prompts.md.

### Original AI-Generated Summary:

In a nutshell

This PR completes the UserDTO implementation and updates the OrderController plus related documentation. It’s a small, single-commit change set that’s open and currently mergeable.
Summary

Title: Complete UserDTO and OrderController with documentation updates
Author: LalithaGayathri
PR: #1 — https://github.com/LalithaGayathri/m3-hands-on/pull/1
State: open (not a draft)
Commits: 1
Files changed: 3
Additions / Deletions: +80 / -3
Comments / Review comments: 0 / 0
Requested reviewers: none
Mergeable: true (mergeable_state: clean)
CI / checks: no check-run status present in the PR metadata I fetched (I can fetch check runs if you want)
Risk assessment: Low–Medium — most changes are DTO and docs (low), but OrderController is runtime code and could affect behavior or APIs (medium). Recommend tests/review focused on controller behavior and API compatibility.

## Edited PR Summary

### Summary

This PR completes the `UserDTO` implementation and the missing `OrderController` methods using GitHub Copilot suggestions. It also documents the Copilot autocomplete observations in `Prompts.md`.

### Changes

- Implemented `UserDTO.fromUser(User)` to map a `User` object to a `UserDTO`.
- Implemented `OrderController.getOrderById(long)` using the order store.
- Implemented `OrderController.createOrder(String, int)` with input validation, ID allocation, storage, and return of the newly created order.
- Added a test execution record confirming that all 4 available tests passed.
- Documented the Copilot-generated suggestions and observations in `Prompts.md`.

### Verification

- Java 17 compilation completed successfully.
- All 4 JUnit tests passed.