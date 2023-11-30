# 01 Singleton Design Pattern

<!-- Def
Problem Statement (Why?)
How to Implement (How?)
Pros
Cons -->

## Definition

- It allows you to create a class for which only one object can be created.
- `Singleton:` Class for only one objects can be created.

---
## Why to Use it?

- A class which is having a shared resource behind the scenes.
    - Ex. We need `db Connection` in our package for different different classes
    - So it's not a good way to create a db connection for every class.
    - Instead we should create one connection and use it's object in every class.
    - So it sounds better to use a single single db connection object across all the services.
    - When we have a diff db connection such as mongo or sql then we will create a another object for it.
- Creation of an object is expensive and only 1 object is needed.
- Singletons are always immutable.

---
## How to Implement?

1. Make constructor private.
2. Create a static method to create an instance.
3. Static method checks of the instance is already created.
    - If yes --> Return Instance
    - If no --> Create new instance and return it.

---
## Singleton in Concurrent Environment

### Early Loading / Eager Execution

- Object is created when class is loaded (application is started).

#### cons
- App startup will be slow
- Can't pass the parameters while creating the first instance.

### Problem Statement

1. How will it implement in multi threaded environment?
    - We have two threads checking the same if (instance == null) condition for the first time.
    - Both of will create a instance and that will be breaker for singleton.
    - This is problem when the obj. is created for the first time.

### Solution

#### Double Check Locking (DCL)
- It will take a lock on the second condition.

```java
if (instance == null) {
    
    Lock()
        if (instance == null) {
            instance = new DBC();
        }
    Unlock()

}
```

---
## Pros

1. Resource Efficiency
2. Creating a new object is inefficient

---
## Cons

1. Difficulty in testing a singleton class (because we need to create mock object to test and we cannot create more than one object).
