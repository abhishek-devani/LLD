### Open/Closed Principle (OCP):

The Open/Closed Principle is one of the SOLID principles of object-oriented design, stating that a class should be open for extension but closed for modification.

**Example:**
Consider a drawing application that can draw different shapes (circles, squares, etc.). Initially, you might have a class like this:

```java
public class Drawing {
    public void drawCircle() {
        // draw circle
    }

    public void drawSquare() {
        // draw square
    }
}
```

Now, let's say you want to add a new shape, a triangle. Instead of modifying the existing `Drawing` class, you can follow the OCP by introducing an interface or abstract class:

```java
public interface Shape {
    void draw();
}
```

Then, you can create specific shape classes that implement this interface:

```java
public class Circle implements Shape {
    public void draw() {
        // draw circle
    }
}

public class Square implements Shape {
    public void draw() {
        // draw square
    }
}

public class Triangle implements Shape {
    public void draw() {
        // draw triangle
    }
}
```

Now, the `Drawing` class can work with any shape that implements the `Shape` interface without modifying its code:

```java
public class Drawing {
    public void drawShape(Shape shape) {
        shape.draw();
    }
}
```

Certainly! To draw a circle using the classes and interfaces mentioned earlier, you can do the following in the `main` function:

```java
public class Main {
    public static void main(String[] args) {
        // Create a Drawing instance
        Drawing drawing = new Drawing();

        // Create a Circle instance
        Circle circle = new Circle();

        // Draw the circle using the Drawing instance
        drawing.drawShape(circle);
    }
}
```

In this example, the `main` function creates an instance of the `Drawing` class and a `Circle` instance. It then calls the `drawShape` method of the `Drawing` class, passing the `Circle` instance as an argument. This demonstrates how you can draw a circle without modifying the existing code, adhering to the Open/Closed Principle.

This way, you can extend the application to support new shapes without modifying existing code, adhering to the Open/Closed Principle.