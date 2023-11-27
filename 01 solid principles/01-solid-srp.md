# Single Responsibility Principle (SRP):

> This principle states that a class should have only one reason to change, meaning it should have only one responsibility.

**Example:**
Consider a class called `Report` that is responsible for both generating a report and saving it to a file. This violates the SRP because the class has more than one responsibility.

```java
public class Report {
    public void generateReport() {
        // Generate the report
    }

    public void saveToFile() {
        // Save the report to a file
    }
}
```

A better design adhering to SRP would be to separate these responsibilities into two classes:

```java
public class ReportGenerator {
    public void generateReport() {
        // Generate the report
    }
}

public class ReportSaver {
    public void saveToFile() {
        // Save the report to a file
    }
}
```
    
Now, each class has a single responsibility, making the code more modular and easier to maintain. If there are changes to how reports are generated or saved, it's less likely to affect both parts of the system.