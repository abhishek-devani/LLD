# Interface Segregation Principle (ISP):

- It states that a class should not be forced to implement interfaces it does not use. 
- In other words, a class should only be required to implement the methods that are relevant to its behavior.
- This principle is particularly relevant when dealing with interfaces. It suggests that large, monolithic interfaces should be split into smaller, more specific interfaces so that classes can choose to implement only the interfaces that are relevant to them.


**Example:**

Consider an initial design where there is a broad interface `Worker` that includes methods for both a regular worker and a manager:

```java
// Worker interface
interface Worker {
    void work();
    void eat();
    void manage();
}

// RegularWorker class
class RegularWorker implements Worker {
    public void work() {
        // Working logic
    }

    public void eat() {
        // Eating logic
    }

    public void manage() {
        // Regular worker should not have managerial responsibilities
    }
}

// Manager class
class Manager implements Worker {
    public void work() {
        // Managing logic
    }

    public void eat() {
        // Eating logic
    }

    public void manage() {
        // Managing logic
    }
}
```

In this scenario, the `RegularWorker` is forced to implement the `manage` method, even though it's not applicable to regular workers.

Now, let's apply the Interface Segregation Principle by splitting the `Worker` interface into more specific interfaces:

```java
// Workable interface
interface Workable {
    void work();
}

// Eatable interface
interface Eatable {
    void eat();
}

// Manageable interface
interface Manageable {
        void manage();
}

// RegularWorker Class
class RegularWorker implements Workable, Eatable {    
    public void work() {        
        // Working logic    
    }  
      
    public void eat() {        
        // Eating logic    
    }
}

// Manager class
class Manager implements Workable, Eatable, Manageable {    
    public void work() {        
        // Managing logic    
    }

    public void eat() {        
        // Eating logic    
    }

    public void manage() {        
        // Managing logic    
    }
}

// Main class
public class Main {
    public static void main(String[] args) {

        RegularWorker regularWorker = new RegularWorker();
        Manager manager = new Manager();

        regularWorker.work();
        regularWorker.eat();

        manager.work();
        manager.eat();
        manager.manage();

    }
}
```

Now, classes can implement only the interfaces that are relevant to their behavior. This adheres to the Interface Segregation Principle, making the design more flexible and preventing classes from being burdened with unnecessary methods.