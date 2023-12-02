# Prototype Design Pattern (Registry Design Pattern)

The Prototype design pattern is a creational pattern that allows you to create new objects by copying an existing object, known as the prototype.

## Use Cases

- When most of the things are fixed and some of them is changing we can use Prototyoe desing patter.
- Ex. Search API Call
    - `url:` fixed
    - `path:` fixed
    - `token:` fixed
    - `queryString:` changes

---
## How to use?

- Often where we don't want to create an object from scratch.
- Rather, we prefer creating from an existing template / prototype and change specific values.

---
## Code

- [Prototype Design Pattern](https://github.com/abhishek-devani/java-concepts/tree/main/src/designPatterns/prototype)