# Code Review and Refactoring

## Introduction

In this session, you will learn the importance of code review and refactoring in maintaining high-quality code. Code review helps identify potential issues, improve code quality, and share knowledge among team members. Refactoring improves the structure and readability of the code without changing its functionality.

## Objectives

1. **Understand Code Review**: Learn the purpose and process of code review.
2. **Identify Code Smells**: Recognize common code smells that indicate the need for refactoring.
3. **Refactor Code**: Apply refactoring techniques to improve code quality.

## Code Review Process

### What is Code Review?

Code review is the process of examining code written by others to identify potential issues, ensure adherence to coding standards, and improve overall code quality. It involves providing constructive feedback and suggestions for improvement.

### Steps in Code Review

1. **Preparation**: Understand the context and purpose of the code.
2. **Examine Code**: Look for potential issues such as bugs, code smells, and non-adherence to coding standards.
3. **Provide Feedback**: Offer constructive feedback and suggest improvements.
4. **Follow-Up**: Ensure that the feedback is addressed and the code is updated accordingly.

### Real-World Analogy

Think of code review as proofreading an important document. Just as you would check for grammar, spelling, and clarity in a document, you review code for errors, readability, and adherence to coding standards. Just like a well-proofread document is easier to read and understand, well-reviewed code is easier to maintain and extend.

### Example

**Before Review**:
```java
public class User {
    public String name;
    public int age;

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void displayInfo() {
        System.out.println("Name: " + name + ", Age: " + age);
    }
}
```

**After Review**:
```java
public class User {
    private String name;
    private int age;

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void displayInfo() {
        System.out.println("Name: " + name + ", Age: " + age);
    }

    // Added getters and setters for encapsulation
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```
✅ Improvement:
- Changed fields from public to private.
- Added getters and setters for data protection.
- Improved encapsulation for better code quality.

## Refactoring Techniques

### What is Refactoring?

Refactoring is the process of improving the structure and readability of code without changing its functionality. It helps make the code more maintainable and easier to understand.

### Common Refactoring Techniques

1. **Extract Method**: Break down large methods into smaller, more manageable methods.
2. **Rename Variable**: Use meaningful names for variables to improve readability.
3. **Encapsulate Field**: Use getters and setters to access class fields instead of making them public.
4. **Simplify Conditional Logic**: Use early returns or switch statements to make logic easier to follow.
5. **Remove Duplicates*: Reuse methods instead of repeating code.

### Real-World Analogy

Imagine refactoring as reorganizing a cluttered room. You don't throw anything away; instead, you put things in their proper places to make the room more organized and easier to navigate. Similarly, refactoring reorganizes code to make it cleaner and more understandable.

### Example

**Before Refactoring**:
```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

**After Refactoring**:
```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    // Extracted method for subtraction
    public int subtract(int a, int b) {
        return a - b;
    }
}
```
✅ Improvement:
- Code is modular and easier to extend.
- New methods can be added without changing existing logic.

## 🧾 Summary
By the end of this session, you should be able to:
- Understand the importance of code reviews for quality and collaboration.
- Identify code smells that need refactoring.
- Apply refactoring techniques to clean up and improve your code.

Remember: Clean code = Professional code.

---

<div style="width: 100%">
<a href='index.md'><-- Previous Section: Final Project & Career Readiness</a>
<div align="right"><a href='debugging-and-handling-test-failures.md'> Next Section: Debugging and Handling Test Failures --></a></div>
</div>
