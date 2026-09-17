# Lesson03-Primitive Datatype and Variable

### **Table of Contents**

- [Lesson03-Primitive Datatype and Variable](#lesson03-primitive-datatype-and-variable)
    - [**Table of Contents**](#table-of-contents)
  - [1. Keywords](#1-keywords)
  - [2. Variables](#2-variables)
  - [3. Primitive Data Type](#3-primitive-data-type)
    - [3.1 Integral](#31-integral)
    - [3.2 Floating](#32-floating)
    - [3.3 Boolean](#33-boolean)
  - [4. Naming Rules](#4-naming-rules)
  - [5. Initialization](#5-initialization)
  - [6. Scope and Lifetime of a Variable](#6-scope-and-lifetime-of-a-variable)
  - [7. Escape Sequence](#7-escape-sequence)
  - [8. Keep Code Clean 2](#8-keep-code-clean-2)
    - [8.1 Appropriate Names](#81-appropriate-names)
    - [8.2 Add Spaces](#82-add-spaces)
    - [8.3 Add Empty Lines](#83-add-empty-lines)
    - [8.4 Avoid Using Magic Numbers](#84-avoid-using-magic-numbers)
  - [9. Auto-completion](#9-auto-completion)

## 1. Keywords

A **keyword** is a reserved Java word with a meaning defined by the language itself.

Java is case-sensitive, and this rule applies to keywords. For instance, `int` (all lowercase) is a valid keyword, whereas `Int` (with a capital “I”) is not. Keywords cannot be redefined by the programmer.

In IntelliJ, keywords are highlighted in orange. Examples encountered in the Hello World project include:
1.	`package`: Specifies the package to which a file belongs. Packages help organize classes, and in large projects, placing all files in a single package is impractical.
2.	`public`: An access modifier that determines which parts of the code can access a particular element. A `public` member can be accessed from any class within the project.
3.	`class`: Declares that the following structure is a class.
4.	`static`: Indicates that a member belongs to the class itself rather than to an instance of the class.
5.	`void`: Denotes that a method does not return a value.

A complete list of Java keywords is available in the official documentation. For now, we will gradually introduce the most commonly used keywords.

## 2. Variables

Variables give a program named places in which to store information.

When a variable is defined in a program, it can be accessed using the name assigned to it. The computer automatically manages the storage location in the system’s Random Access Memory (RAM). For example:

```java
int num = 5;
```

In this example, a variable named `num` is defined and assigned the value 5. Once defined, the variable num can be used to directly access this value.


A variable contains three parts:

1. data type
2. name
3. value

## 3. Primitive Data Type

When defining a variable, it is necessary to specify its data type—whether it is an integer, a floating-point value, or a character. **Primitive data** types in Java are predefined, and there are eight of them. All primitive data types are reserved keywords in the language.

| Data Type | Value    | Size |
| --------- | -------- | ---- |
| byte      | integral | 1    |
| short     | integral | 2    |
| char      | integral | 2    |
| int       | integral | 4    |
| long      | integral | 8    |
| float     | floating | 4    |
| double    | floating | 8    |
| boolean   |          |      |

Each primitive data type has a corresponding *wrapper class*, e.g., `int` -> `Integer`, `double` -> `Double`, and `boolean` -> `Boolean`. We will see these classes in the future.

### 3.1 Integral

The first five data types are used to store an integer value, for example

```java
byte num1 = 5;
short num2 = 6;
int num3 = 7;
long num4 = 8L;
```

The primary difference among these integral types is their size in memory. A `byte` variable occupies 1 byte, which equals 8 bits (0s and 1s). The first bit indicates the sign of the number—0 for positive and 1 for negative—while the remaining 7 bits represent the value. Consequently, the range of a byte variable is from -128 to 127, meaning that it cannot store values exceeding 127.

```java
byte num = 128;   // Error, 128 is too big for byte
```

The `short` data type occupies 2 bytes, `int` occupies 4 bytes, and `long` occupies 8 bytes. By default, `int` is used for storing integral values. Only when a number exceeds the range of `int` should `long` be used, and in that case, the value should be suffixed with an `L`. In practice, `byte` and `short` are rarely used.

The `char` data type is used to store a single character, such as `'a'`, `'9'`, or `'!'`. Internally, characters are converted into numbers because numbers can be easily represented in binary. The mapping between characters and numbers can be found in the **American Standard Code for Information Interchange (ASCII) table**. For example, the character `'a'` corresponds to 97, and `'9'` corresponds to 57. While the ASCII table is easily accessible online, memorization is not required. A char value is defined using single quotes (`''`). It is important to note that `'0'` (a character) is different from `0` (a numeric value).

```java
// the following two statements are the same
char character1 = 'a';
char character2 = 97;
```

There are certain special integer values that can be used directly:

| Value                        | Meaning                             | Example                                    |
| ---------------------------- | ----------------------------------- | ------------------------------------------ |
| `Integer.MAX_VALUE`        | the maximum an `int` can reach    | `int num = Integer.MAX_VALUE;`           |
| `Integer.MIN_VALUE`        | the minimum an `int` can reach    | `int num = Integer.MIN_VALUE;`           |

### 3.2 Floating

To store a floating-point number in a variable, a floating-point data type should be used. There are two primary floating-point types:
- `float`: less precise
- `double`: more precise and used by default

In practice, `float` is rarely used. However, if it is necessary, the value assigned to a float variable should be suffixed with an `f`.

```java
float num1 = 3.14f;
double num2 = 3.14;
```

There are certain special floating values that can be used directly:

| Value                        | Meaning                             | Example                                    |
| ---------------------------- | ----------------------------------- | ------------------------------------------ |
| `Double.MIN_VALUE`         | the minimum positive value a `double` can reach | `double num = Double.MIN_VALUE;`         |
| `Double.MAX_VALUE`         | the maximum a `double` can reach   | `double num = Double.MAX_VALUE;`         |
| `Double.POSITIVE_INFINITY` | positive infinity                   | `double num = Double.POSITIVE_INFINITY;` |
| `Double.NEGATIVE_INFINITY` | negative infinity                   | `double num = Double.NEGATIVE_INFINITY;` |
| `Double.NaN`               | not a Number                        | `double num = Double.NaN;`               |

### 3.3 Boolean

The `boolean` data type is a special type that can hold only two possible values: `true` and `false`.


```java
boolean isCorrect = true;
boolean pass = false;
```

The result of comparing two values to check if they are the same is a boolean:

```java
boolean eq = 1 == 1.0;  // true since 1 equals 1.0 
```

Note: `String` is not a primitive data type. All primitive data types are lowercase. If the first character is uppercase, as in `String`, `Integer`, `Boolean`, or `Double`, it is a class.

## 4. Naming Rules

When naming variables in Java, the following rules apply:

1. The name must begin with a letter, underscore `_`, or dollar sign `$`.
2. Subsequent characters may include letters, digits, underscores, or dollar signs.
3. Variable names are case-sensitive (`Score` and `score` are different identifiers).
4. Reserved keywords cannot be used as variable names.

```java
int num1;
int num2;
double avgScore;
double finalScore;
double discountRatio;
```

Technically, numbers may appear anywhere in a variable name except at the very beginning; however, they are typically placed at the end.

Variable names should be self-documenting, meaning they should clearly indicate the purpose of the variable. Avoid ambiguous names such as `x` and `y`.

Standard abbreviations may be used, such as `avg` for average, `str` for string, `idx` for index, and `num` for number. However, do not invent personal abbreviations, as they may not be understood by others. For instance, avoid using `fp` to represent final price.

## 5. Initialization

A variable may be initialized after it is declared, although this is not mandatory. It is possible to declare a variable without assigning a value immediately and provide a value at a later point in the program.

```java
int num1 = 5;  // initialize num1 as 5
int num2;  // num2 has no value yet

// other code
System.out.print(num2); // Error, num2 has no value yet, cannot read it

num2 = 10;  // num2 is assigned after it is created
System.out.print(num2); // print 10
```

A variable’s value cannot be read until it has been initialized.

Additionally, the value of a variable can always be modified after it has been assigned.

```java
int num = 5;
num = 6; // change the value of num
num = 7; // change the value of num again
num = 10; // change the value of num again
```

You may see someone declare variables of the same data type in the same row, but I personally do not recommend it.

```java
int num1 = 3, num2 = 5, num3 = 10;  // not recommended

// recommended
int num1 = 3;
int num2 = 5;
int num3 = 10;
```

## 6. Scope and Lifetime of a Variable

The **scope** of a variable defines the regions of a program where the variable can be accessed, while the **lifetime** of a variable refers to how long it remains in memory.

If a variable is declared within a method, it is called a **local variable**. Such a variable is accessible only within that method and ceases to exist once program control exits the block in which it was declared.

```java
public static void main(String[] args) {
    int num1 = 5; // create a local variable in main
    int num1 = 10;  // error, trying to create another num1 in the same scope

    System.out.print(num2);
    // error, num2 is not defined in this method
}

public static anotherMethod() {
    // num2 is defined in this method
    int num2 = 1;
}
```

## 7. Escape Sequence

Some characters on the keyboard cannot be inserted directly into a String or a char. For example, the `Enter` key cannot be represented as a literal character. Similarly, if you attempt to include a double quotation mark (`"`) directly inside a string, it will cause a compilation error because the compiler interprets it as the end of the string.

```java
// error, the first " will match with the second ", then sure"" is invalid
String str = "He said "sure"";

// error, the first ' will match with the second ' instead of the third '
char character = ''';

// error, directly type enter cannot store it into a string
String str = "
                 ";
```

We can address this issue by using **escape sequences**. An escape sequence is a combination of characters that represents a special character or action, rather than the literal characters themselves. It typically begins with a backslash (`\`) followed by another character.

| Combination | To Represent |
| ----------- | ------------ |
| `\n`      | `enter`    |
| `\t`      | `tab`      |
| `\"`      | `"`        |
| `\'`      | `'`        |
| `\\`      | `\`        |

```java
String str = "He said \"sure\"";  // the first " will match with the last " since the second " and the third " have a \ in front
char character = '\'';    // the first ' will match with the last ' since the second ' has a \ in front
String str = "\n";    // a line breaker is stored in str
String path = "C:\\Users\\yi";   // the path is C:\Users\yi
```

## 8. Keep Code Clean 2

### 8.1 Appropriate Names

Always assign meaningful names to your projects, classes, methods, and variables. Poorly chosen names can create misunderstanding and ambiguity, making the code harder to read, maintain, and collaborate on.

### 8.2 Add Spaces

Just as spaces are required between words in English to ensure readability, proper spacing is also important in Java code. You should include a single space around each keyword, after comma (`,`) and around operators that operate on two values. This practice improves clarity and makes the code easier to read.

```java
// int num1 = 5;   // clean
int    num1 = 5;   // unclean
int num1=5;   // unclean
int num1 =5;    // unclean
int num1 = 5 ;   // unclean
```

### 8.3 Add Empty Lines

Adding empty lines can improve the clarity of your code by visually separating different sections. However, they should be used appropriately and only where they enhance readability, such as grouping related parts of the code into distinct blocks, e.g.:

```java
double num1 = 5;
double num2 = 10;
double num3 = 15;

double sum = num1 + num2 + num3;
double avg = sum / 3;

System.out.println("The sum is " + sum);
System.out.println("The average is " + avg);
```

In this example, two empty lines have been added, effectively dividing the code into three distinct sections. The first section declares the necessary variables, the second performs the required calculations, and the third handles the output of results. This separation significantly enhances readability, allowing the code to be more easily understood and maintained.

**Important: Always put ONE empty line at the end of a file.**

### 8.4 Avoid Using Magic Numbers
Some numbers are immediately understandable, such as `60` and `24` in the context of a clock, and can therefore be used directly in the code. However, other numbers may not be as clear. For instance, a tax ratio of `0.145` lacks inherent meaning; directly embedding such a value in the code can lead to confusion. This type of number is referred to as a magic number, as it appears without explanation, seemingly “magical.” The use of magic numbers reduces code clarity. A better approach is to define a variable with a meaningful name to represent the value, thereby improving readability and maintainability.

```java
// bad since 1.145 is a magic number
double originalPrice = 3.99;
double finalPrice = originalPrice * 1.145;

// good since 1.145 is assigned to a variable with a meaningful name
double originalPrice = 3.99;
double taxRatio = 0.145;
double finalPrice = originalPrice * (1 + taxRatio);
```

## 9. Auto-completion

Using auto-completion while coding is highly recommended. Modern Integrated Development Environments (IDEs) can often predict what you intend to type based on minimal input. For example:

If a variable named `avgScore` has already been defined, typing the letter `a` will trigger a pop-up menu in the IDE. Pressing Enter or Tab will auto-complete the variable name. This feature reduces the likelihood of typographical errors and can significantly accelerate the programming process.

In cases where multiple variables share the same initial letter—such as `avgScore`, `address`, and `appleTyping`—typing additional characters, such as `av`, will narrow the menu to only `avgScore`. Alternatively, you can type `a` and use the arrow keys to select the desired variable for completion.
