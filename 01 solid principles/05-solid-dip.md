# Dependency Inversion Principle (DIP):

- It suggests that high-level modules should not depend on low-level modules, but both should depend on abstractions. 
- Furthermore, abstractions should not depend on details; details should depend on abstractions.
- This principle encourages the use of abstractions (interfaces or abstract classes) to decouple high-level modules from low-level modules, promoting flexibility and ease of change.

**Example:**

Consider a scenario where there's a high-level module (`LightSwitch`) depending directly on a low-level module (`Bulb`). Without applying the Dependency Inversion Principle:

```java
// Bulb class
class Bulb {

    void turnOn() {
        // Bulb-specific logic to turn on
    }

    void turnOff() {
        // Bulb-specific logic to turn off
    }
}


// LightSwitch class
class LightSwitch {

    private Bulb bulb;

    LightSwitch(Bulb bulb) {
        this.bulb = bulb;
    }

    void operate() {
        // Operating the bulb directly
        bulb.turnOn();
        bulb.turnOff();
    }
}
```

In this example, `LightSwitch` depends directly on the concrete implementation of `Bulb`, violating the Dependency Inversion Principle.

Now, let's apply the Dependency Inversion Principle by introducing an abstraction (`Switchable`) that both high-level and low-level modules depend on:

```java
// Switchable interface
interface Switchable {

    void turnOn();

    void turnOff();
}


// Bulb class
class Bulb implements Switchable {

    public void turnOn() {
        // Bulb-specific logic to turn on
    }

    public void turnOff() {
        // Bulb-specific logic to turn off
    }
}


// LightSwitch class
class LightSwitch {

    private Switchable device;

    LightSwitch(Switchable device) {
        this.device = device;
    }

    void operate() {
        // Operating the device through the abstraction
        device.turnOn();
        device.turnOff();
    }
}
```

Now, both `Bulb` and `LightSwitch` depend on the abstraction `Switchable`. This adheres to the Dependency Inversion Principle, as high-level and low-level modules depend on abstractions rather than concrete implementations. This makes it easier to change or extend the system without modifying existing code.

```java
// Main class
public class Main {

    public static void main(String[] args) {
        // Create a Bulb instance
        Bulb bulb = new Bulb();

        // Create a LightSwitch and operate the Bulb
        LightSwitch lightSwitch = new LightSwitch(bulb);
        lightSwitch.operate();
    }
}
```

In the `main` method, a `Bulb` instance is created, and then a `LightSwitch` is created, taking the Bulb instance as a parameter. The `operate` method of the `LightSwitch` is then called, demonstrating how the `LightSwitch` can operate on any device that implements the `Switchable` interface.