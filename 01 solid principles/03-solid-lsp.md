# Liskov's Substitution Principle (LSP):

- It states that objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.
- In simpler terms, if a class is a subclass of another class, it should be able to replace its parent class without affecting the behavior of the program.

**Example:**
Consider a scenario where you have a class hierarchy representing different shapes:

```java
class Shape {
    int area() {
        return 0;
    }
}

class Rectangle extends Shape {
    int width;
    int height;

    @Override
    int area() {
        return width * height;
    }
}

class Square extends Shape {
    int side;

    @Override
    int area() {
        return side * side;
    }
}
```

According to Liskov's Substitution Principle, you should be able to use any subclass (`Rectangle` or `Square`) wherever a parent class (`Shape`) is expected without causing issues. For example:

```java
void printArea(Shape shape) {
    System.out.println("Area: " + shape.area());
}
```

Main Class

```java
public static void main(String[] args) {
    
    Rectangle rectangle = new Rectangle();
    rectangle.width = 5;
    rectangle.height = 10;

    Square square = new Square();
    square.side = 5;

    printArea(rectangle); // Should print the area of the rectangle
    printArea(square); // Should print the area of the square
}
```

In this example, `printArea` method accepts a `Shape` parameter. The ability to pass both `Rectangle` and `Square` instances demonstrates Liskov's Substitution Principle. Each subclass can be used interchangeably with the base class without causing issues in the program's logic.