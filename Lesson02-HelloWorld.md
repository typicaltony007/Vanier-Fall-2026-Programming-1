# Lesson02-HelloWorld

### **Table of Contents**

- [Lesson02-HelloWorld](#lesson02-helloworld)
    - [**Table of Contents**](#table-of-contents)
  - [1. What is `HelloWorld`](#1-what-is-helloworld)
  - [2. Project, Class, Statement](#2-project-class-statement)
  - [3. Creating a Project in IntelliJ IDEA](#3-creating-a-project-in-intellij-idea)
    - [3.1. Naming System](#31-naming-system)
  - [4. Project Structure](#4-project-structure)
  - [5. `main()` method](#5-main-method)
  - [6. `Sout` statement](#6-sout-statement)
  - [7. Executing Code](#7-executing-code)
  - [8. Comments](#8-comments)
    - [8.1 Single-line Comment](#81-single-line-comment)
    - [8.2 Multi-line Comment](#82-multi-line-comment)
    - [8.3 Documentation (Javadoc)](#83-documentation-javadoc)
  - [9. Keep Code Clean 1](#9-keep-code-clean-1)
    - [9.1 Indent](#91-indent)
    - [9.2 Avoid Long Line Code](#92-avoid-long-line-code)
  - [10 How to Find Your Project](#10-how-to-find-your-project)

## 1. What is `HelloWorld`

In many programming courses, the first program prints “Hello World” on the screen.

This simple exercise has two practical purposes:

- It tests whether your setup (editor, compiler, runtime) works correctly.
- It allows you to practice creating, compiling, and running a program with minimal complexity.

The goal isn’t the phrase itself, but confirming that every part of the development environment is connected and functioning.

## 2. Project, Class, Statement

When programming in an IDE, code is organized into projects and files:
- A project serves as a container for your work and can include multiple files, such as classes, interfaces, enums, and more.
- In this course, we will primarily work with classes, although interfaces and other file types will be introduced later.
- A class contains methods (blocks of code that perform specific actions) and statements (individual instructions).

This structure can be compared to preparing a large family meal:
- The meal represents the project.
- Each dish represents a class.
- Each ingredient or step in the recipe represents a statement.

A statement is a complete instruction that the computer executes. While it may contain one or more expressions, it must always terminate with a semicolon (`;`).

```java
// Here, int num = 3; is a statement. It declares a variable named num and assigns it the value 3.
int num = 3;
```

## 3. Creating a Project in IntelliJ IDEA

In IntelliJ, you can create a new project by providing an appropriate project name, selecting a convenient location (the `Downloads` folder is recommended), and configuring the following settings:
- Language: `Java`
- Build system: `Maven`
- JDK: `21` or any other LTS JDK version

The choice of build system does not affect the Java language itself, but it does influence the project structure. Further details on Maven will be covered later in the course.

If the Add sample code option is selected, a Main class with a small piece of sample code will be generated automatically. However, do not select the Generate code with onboarding tips option.

Expand the Advanced Settings and change the **GroupId** from `org.example` to a personalized value, such as `org.yourname` (e.g., `org.yi`). The **GroupId** determines the default package name of your project. A package is essentially a directory, and organizing different files into separate packages helps maintain clean and well-structured code.

### 3.1. Naming System

In Java, names must be assigned to many elements, including projects, classes, methods, and variables. There are specific naming conventions that should be followed to ensure clarity and consistency.
- Projects, classes, and variables should generally be **nouns**, possibly preceded by an adjective (e.g., `Dog` or `HappyDog`).
- If a name consists of multiple words, no spaces should be used, and the first character of each word should be capitalized. This style is known as **camel case**.
- For projects and classes, the first character of the name should be uppercase.
- For variables and methods, the first character should be lowercase.
- Method names should typically be **verbs** to indicate an action.

Examples include:


* Project or Class: `Dog` `HappyDog`
* Variable: `dog` `happyDog`
* Method: `equals` `toString`

## 4. Project Structure

If we select `Maven` as the project build system, then the structure of the project would look like:

``` bash
Project
|-.idea
|-src
| |-main
| | |-java              // write code in this folder
| | |-resources
| |
| |-test
|   |-java
|   |-resources
|
|-target
|-.gitignore
|-pom.xml
```

where

* `.idea` is a directory for IntelliJ project settings, and we will not touch it.
* `src/main/java` is the directory for the source code
* `src/main/resources` is the directory for external files that your source code may need, usually data files
* `src/test/java` is the directory for source code for testing
* `src/test/resources` is the directory for testing data
* `target` is the directory for generated files, such as `.class` and `.jar`
* `.gitignore` is a file that lists all files that we do not want to update to the repository when using git version control.
* `pom.xml` is the Maven project configuration file.

This semester we will first focus on `src/main/java`, and then introduce `src/test/java`, `.gitignore`, and `pom.xml` later.

## 5. `main()` method

A project may contain multiple files, and each file may contain multiple methods. Analogous to a meal with many dishes, it is important to know where to start—certainly not with dessert. Each code block is enclosed within a pair of curly braces `{}`.

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

Java begins execution at the `main()` method. Whenever a word is followed by a pair of parentheses, `xxx()`, it indicates a method. A method is a collection of statements designed to perform a specific operation. For example, a method `cleanTable()` could consist of several steps: removing all items from the table, wetting the mop, cleaning the table, and returning the items to their original positions.

The parameter `String[] args` in `main()` is the formal parameter, where `args` stands for arguments.

In IntelliJ, you can generate a `main()` method using the shortcut `psvm + Tab`. The acronym psvm represents the four starting keywords of the `main()` method: `public`, `static`, `void`, and `main`.

Technically, a project can have zero, one, or multiple `main()` methods. For learning purposes, we will begin with a single `main()` method.

## 6. `Sout` statement

For this project, the only statement required is:

```java
System.out.println("Hello World");
```

This statement calls the `System.out.println()` method from the JDK, which prints the provided content to the console. The content to be printed is passed as an argument within the parentheses `()`.

The method name `println` stands for “print line.” If the `ln` is removed, the statement becomes `System.out.print()`, which prints the content without adding a line break at the end.

In IntelliJ, the shortcut `sout + Tab` can be used to automatically generate a `System.out.println()` statement, which is why this chapter is referred to as `sout`.

The text `"Hello World"` is a string. In Java, a string is enclosed in double quotes `""` and is immutable, meaning its value cannot be changed after it is created.

## 7. Executing Code

Once the code is complete, it must be executed to verify that the output matches the expected result. Execution can be performed by clicking the green triangle button in the IDE or by using the shortcut `Shift + F10` on Windows.

The term **run** or **execute** encompasses several steps: linking code from different files, compiling it into binary form, executing the compiled code, and displaying the output in the console.

A black window, called the console, appears at the bottom of the IDE, where the program output can be observed. For example, the message `Hello World` may be printed.

The message `Process finished with exit code 0` indicates that the code executed successfully without errors. Conversely, a nonzero exit code signifies that an error occurred during execution.

## 8. Comments

Comments are text ignored by the Java compiler. You can write comments to explain your code, so others or yourself can understand it better.

There are three different comments in Java:

### 8.1 Single-line Comment

Single-line comments are the most commonly used type of comment. Any text following `//` on the same line is treated as a comment. Single-line comments can be placed either above the code they describe or to the right of a short statement. For example:

```java
int finalGrade;   // the final grade the student gets
int avgScore;   // the average score the student gets

// calculate the average score
avgScore = (score1 + score2 + score3 + score4) * assignmentWeight + (score5 + score6) * examWeight;
```

Single-line comments can also be used to temporarily disable code. For instance, if a piece of code produces unexpected results, deleting it may make it difficult to restore later. Instead, commenting out the code allows the compiler to ignore it while keeping it accessible. To restore the code, simply remove the `//` at the beginning of the line.

In IntelliJ, the shortcut to comment or uncomment code is `Ctrl + /`. This shortcut can be applied to multiple lines simultaneously.

### 8.2 Multi-line Comment

A multi-line comment starts with `/*` and ends with `*/`. Any text between `/*` and `*/` will be ignored by Java. Usually, it is used if the comment is long.

```java
/*
This is a long comment that may cross multiple lines
I am still a comment
Me too
*/
```

### 8.3 Documentation (Javadoc)

Javadoc in Java is used at the class, interface, enum, or method level to explain the purpose and functionality of the element. Documentation comments begin with `/**` and end with `*/`. It is considered good practice to provide documentation for every class, interface, enum, and method, except in cases where the functionality is self-evident, such as the `main()` method.

The following shows an example of documentation for a method.

```java
/**
 calculates the sum of the elements of a double array.
 @param nums the input double array
 @return the sum of the elements of the input double array
 */
public static double calcSum(double[] nums) {
     // code inside
}
```

Further details on documentation will be provided when we study methods and classes in more depth.

## 9. Keep Code Clean 1

Maintaining clean code is of paramount importance. Even if the code is functionally correct, poor formatting can make it difficult for others to understand and maintain. Analogous to a novel, no matter how engaging the story is, a text without line breaks or spacing between words would be virtually unreadable. While the content remains technically the same, readability suffers significantly.

### 9.1 Indent

There are several conventions for keeping code clean. One basic rule is to indent `B` by one level from `A` if `B` is a component of `A`. For instance:
- Methods are part of a class, so method definitions should be indented one level relative to the class.
- Statements are part of a method, so statements should be indented one level relative to the method.

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello world!");
    }
}
```

### 9.2 Avoid Long Line Code

In the editor, you may notice a vertical guideline on the right side. This line serves as a visual aid to help you maintain shorter, more readable code. Typically, the guideline is set at 80, 100, or 120 characters. It is recommended to keep your code to the left of this line.

If a statement is too long to fit within this limit, consider splitting it into multiple lines. The continuation lines should be indented appropriately—typically **two levels**—for clarity.

```java
System.out.println(1 + 2 + 3 + 4 + 5 + 6 + 7
        + 8 + 9 + 10 + 11 + 12 + 13 + 14 + 15);
```

## 10 How to Find Your Project

After creating a project in IntelliJ, it is stored on your computer. For example, if the HelloWorld project was saved on the Desktop, a directory named `HelloWorld` will appear there, containing the project structure as described in [Chapter 4](#4-project-structure).

The project includes many files automatically generated by IntelliJ; however, only the source code located in `src/main/java` is authored by you. When submitting homework, you should submit only the source files, not the entire project directory, unless a specific requirement is given.
