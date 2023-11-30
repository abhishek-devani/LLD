# 02 Builder Design Pattern

## Definition

- It allows for the step-by-step construction of complex objects.
- It separates the construction fof an object from its representation.

---
## Why to Use it?

- When you have a class with a lot of attributes.
- When we want to validate the object of a class even before creating the object.
- When we are taking inputs from user.

### Validation Example

- No Student with grad Year >= 2022
- Phone np. should be 10 digit only
- grad year >= age + 2000

---
## How to Implement?

1. Create a `Builder` class
2. Define all the `attributes` in builder class and validate using builder class.
3. Pass the object of `builder` class to `Student` class.

---
## Code

- [Builder Design Pattern](https://github.com/abhishek-devani/java-concepts/tree/main/src/designPatterns/builder)