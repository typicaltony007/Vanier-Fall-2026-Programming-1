# Lesson06-String

### Table of Contents

- [1. String](#1-string)
  - [1.1 What Is A String](#11-what-is-a-string)
  - [1.2 Index System](#12-index-system)
  - [1.3 String Concatenation](#13-string-concatenation)
  - [1.4 `printf()` Method](#14-printf-method)
  - [1.5 String Methods](#15-string-methods)
- [2. Console Input](#2-console-input)

## 1. String

### 1.1 What Is A String

Java’s `String` type stores text. Unlike `int`, `double`, and `char`, it is not primitive; **`String` is a class**.

This means:
- A String variable is actually an **object**.
- Since it’s a class, String comes with many useful methods you can directly use (like finding the length, converting to uppercase, or extracting a part of the text).

A String is written between a pair of double quotes (`"`).

```java
String str1 = "Hello";   // str1 and str2 are objects
String str2 = "";    // empty string
```

Each String object has a length, which tells you how many characters it contains.
- `"hello"` → length 5
- `"000"` → length 3
- `" "` (just a space) → length 1
- `""` (empty string) → length 0

In Java, we use the method `.length()` to get the length:

``` java
System.out.println("hello".length());  // prints 5
System.out.println("000".length());    // prints 3
System.out.println(" ".length());      // prints 1
System.out.println("".length());       // prints 0
```

### 1.2 Index System

Each character in a string has an index, which indicates its position in the string.
- In Java, the index system always starts at **0**.
- The index of the first character is 0, the second is 1, and in general, the index of the n-th character is n - 1.
- The index is always a non-negative integer.
- The value at that index can be any character.

```java
"HelloWorld"  // value
 0123456789   // index
```

To access a character by its index, use the `.charAt()` method:

```java
String text = "HelloWorld";

System.out.println(text.charAt(0));  // prints 'H'
System.out.println(text.charAt(4));  // prints 'o'
System.out.println(text.charAt(9));  // prints 'd'
```

If you try to access an index outside the range `[0, length - 1]`, Java will throw a `StringIndexOutOfBoundsException`.

### 1.3 String Concatenation

String only supports one operation: the concatenation. When you apply `+` on two strings, it joins them together:

```java
String str1 = "Hello";
String str2 = "World";

String str3 = str1 + str2;  // "HelloWorld"
```

**Concatenating with Other Types**

Any value in Java can be converted to a String and then concatenated:

```java
String str1 = "Hello";
int num1 = 3;
double num2 = 3.14;
char character = '!';
boolean flag = true;

System.out.print(str1 + num1);  // "Hello" + 3 -> "Hello" + "3" -> "Hello3"
System.out.print(str1 + num2);  // "Hello" + 3.14 -> "Hello" + "3.14" -> "Hello3.14"
System.out.print(str1 + character); // "Hello" + '!' -> "Hello" + "!" -> "Hello!"
System.out.print(str1 + flag);  // "Hello" + true -> "Hello" + "true" -> "Hellotrue"
```

**Be Careful with Order**

When mixing numbers and strings, the order matters.
Java evaluates from left to right, unless parentheses change the order:

```java
String str = "Hello";

System.out.print(str + 1 + 2);   // ("Hello" + 1) + 2-> "Hello1" + 2 -> "Hello12"
System.out.print(str + (1 + 2));  // "Hello" + 3 -> "Hello3"
System.out.print(1 + 2 + str);   // 3 + "Hello"-> "3Hello"
```

If you need clear string building (especially in loops), prefer `StringBuilder` later. But for now, `+` is enough.

### 1.3 Conversion Between String and Other Data Type

#### 1.3.1 Convert A Value To String

There are two ways to convert a value to a string:

1. `"" + value`: for example, `"" + 3` equals `"3"`
2. `String.valueOf()`: for example, `String.valueOf(3)` equals `"3"`

#### 1.3.2 Convert A String To A Value

Sometimes we need to convert a String into another data type.
- Not all strings can be converted: "Hello" cannot become an `int`.
- But "3" can be converted to 3, "3.14" to 3.14, and "true" to `true`.

To do this, we use the wrapper class of the target type.

| Method                      | Usage                        | Example                        | Result |
| --------------------------- | ---------------------------- | ------------------------------ | ------ |
| `Integer.parseInt(str)`     | convert `str` to an `int`    | `Integer.parseInt("3")`        | `3`    |
| `Double.parseDouble(str)`   | convert `str` to a `double`  | `Double.parseDouble("3.14")`   | `3.14` |
| `Boolean.parseBoolean(str)` | convert `str` to a `boolean` | `Boolean.parseBoolean("true")` | `true` |

These conversions only succeed if the String is valid for the target type.
- `Integer.parseInt("123")` → works.
- `Integer.parseInt("Hello")` → throws an exception (`NumberFormatException`).


### 1.4 `printf()` Method

#### 1.4.1 General Syntax

Previously, we learned how to use `print()` and `println()` to display results in the console. With string concatenation, we can combine variables and text to make the output clearer.

```java
int num1 = 3;
int num2 = 5;

int sum = num1 + num2;

System.out.print(num1 + " + " + num2 + " = " + sum); // print 3 + 5 = 8
```

However, this approach has some drawbacks. In the example above, `num1`, `num2`, and `sum` are variables, while `" + "` and `" = "` are strings. To join everything together, we must use `+` multiple times. Notice:
- 4 concatenations are required.
- Extra spaces must be carefully added around `+` and `=`.

This makes the code harder to write and read, especially for longer or more complex output.

To solve this, Java provides a third way: the `printf()` method.
It is more powerful than `print()` and `println()`, and it allows us to format the output neatly.

The general idea of `printf()` is:
- The first part defines the overall format (the “template”).
- The second part supplies the values to fill into the template.

For example, suppose we want to print `x + y = z`, where `x`, `y`, and `z` are integers.
We can write:

```java
System.out.printf("%d + %d = %d", x, y, z);
```

Here `%d` is a placeholder that will later be replaced by an integer value.
Different data types use different placeholders:

| Type     | Place Holder |
| -------- | ------------ |
| `int`    | `%d`       |
| `char`   | `%c`       |
| `double` | `%f`       |
| `String` | `%s`       |

Since our format string has three placeholders (`%d` + `%d` = `%d`), we must provide three values.
The first placeholder is replaced by `num1`, the second by `num2`, and the third by `sum`.

```java
int num1 = 3;
int num2 = 5;

int sum = num1 + num2;

System.out.print(num1 + " + " + num2 + " = " + sum); // print 3 + 5 = 8
System.out.printf("%d + %d = %d", num1, num2, sum);
```

#### 1.4.2 Formatting

We can also use `printf()` to format values when printing.

For example, if we want to display a floating-point number with two decimal digits after the dot, we can use `%.2f` instead of `%f`. Here, `.2` indicates that 2 decimal places should be displayed.

```java
double price = 3.99;
double taxRatio = 0.145;
double totalPrice = price * (1 + taxRatio);  // 4.56855

System.out.print("Total price: $" + totalPrice);  // print Total price: $4.56855
System.out.printf("Total price: $%.2f", totalPrice);  // print Total price: $4.57
```

Key points
1.	`%f` is for floating-point numbers.
2.	`%.2f` rounds the number to 2 decimal places.
3.	`printf()` does not automatically add a newline, add `\n` at the end of the format string to move to the next line: 

```java
System.out.printf("Total price: $%.2f\n", totalPrice);
```

Here’s a compact table showing common `printf()` formatting examples in Java:

| Value Type      | Format Placeholder | Example Code                                                         | Output                             |
| --------------- | ------------------ | -------------------------------------------------------------------- | ---------------------------------- |
| `int`           | `%d`               | `int x = 5; System.out.printf("x = %d\n", x);`                       | `x = 5`                            |
| `double`        | `%f`               | `double y = 3.14159; System.out.printf("%.2f\n", y);`                | `3.14`                             |
| `String`        | `%s`               | `String name = "Alice"; System.out.printf("%s\n", name);`            | `Alice`                            |
| `char`          | `%c`               | `char ch = 'A'; System.out.printf("%c\n", ch);`                      | `A`                                |
| `int` padded    | `%5d`              | `int x = 42; System.out.printf("%5d\n", x);`                         | `"   42"` (padded to width 5).     |
| `double` padded | `%8.2f`            | `double price = 3.5; System.out.printf("%8.2f\n", price);`           | `"    3.50"` (width 8, 2 decimals) |
| left alligned   | `%-6s`             | `String title = "Name"; System.out.printf("%-6s:%6s", title, name);` | `"Name  :    yi"`                  |
| newline	      | `\n`               | `System.out.printf("Hello\nWorld\n");`                               | `HelloWorld`                       |
| `%` character   | `%%`               | `int tipRate = 15; System.out.printf("%d%%\n");`                     | `15%`                              |

Notes:
- Width (like 5 or 8) pads spaces to align numbers.
- `.2` after `%` rounds floating numbers to 2 decimals.
- `printf()` gives precise control over formatting, unlike `print()` or `println()`.

#### 1.4.3 Zero-padding

If we need to display time, sometimes the hour, minute, or second has only one digit. In such cases, we usually add a 0 in front to keep the format consistent. Adding zeros in front does not change the value, and this is called zero-padding. In `printf()`, we can achieve this by using `%02d` instead of `%d`, where 2 indicates the total length of the number, and if there is an empty place, it will be filled with 0.

```java
int hr = 3;
int mi = 30;
int se = 0;

System.out.print(hr + ":" + mi + ":" + se);   // print 3:30:0
System.out.printf("%02d:%02d:%02d", hr, mi, se);  // print 03:30:00
```

You can use `souf` + `tab` to create `printf()` quickly in IntelliJ.

Notice: since `%` is used to define a placeholder in `printf()` method, to print a normal `%` symbol, we need to use two percentage symbols `%%`.

```java
double ratio = 0.05;
System.out.printf("%.2f = %.1f%%\n", ratio, ratio * 100);       // prints 0.05 = 5.0%
```

### 1.5 String Methods

String class provides us with plenty of methods that can be used on String.

#### 1.5.1 `str.length()`

`str.length()` returns the length of a string, e.g., `"hello".length()` returns `5`. `"".length()` returns `0`.

#### 1.5.2 `str.charAt(idx)`

`str.charAt(idx)` returns the character at that index in `str`, e.g., `"hello".charAt(0)` returns `'h'`, `"hello".charAt(4)` returns `'o'`. If the given index is too big, an index out of bound exception will be thrown, e.g.: `"hello".charAt(5)`.

#### 1.5.3 `str.indexOf(c)`

`str.indexOf(c)` returns the index of the first occurrence of character `c`, the search starts at index 0, e.g., `"hello".indexOf('h')` returns `0`, `"hello".indexOf('l')` returns `2`. If the string does not contain character `c`, then a special value of `-1` will be returned, e.g., `"hello".indexOf('z')` returns `-1`.

#### 1.5.4 `str.indexOf(c, startIdx)`

`str.indexOf(c)` returns the index of the first occurrence of character `c`, the search starts at index `startIdx`, e.g., `"abcabcabc".indexOf('a', 1)` returns `3`, `"abcabcabc".indexOf('a', 4)` returns `6`. If the string does not contain character `c` after the start index, then a special value of `-1` will be returned, e.g., `"abcabcabc".indexOf('a', 7)` returns `-1`.

#### 1.5.5 `str.lastIndexOf(c)`

`str.lastIndexOf(c)` returns the index of the last occurrence of character `c`, the search starts at index `len - 1`, e.g., `"hello".lastIndexOf('h')` returns `0`, `"hello".lastIndexOf('l')` returns `3`. If the string does not contain character `c`, then a special value of `-1` will be returned, e.g., `"hello".lastIndexOf('z')` returns `-1`.

#### 1.5.6 `str.lastIndexOf(c, startIdx)`

`str.indexOf(c)` returns the index of the last occurrence of character `c`, the search starts at index `startIdx`, e.g., `"abcabcabc".lastIndexOf('a', 1)` returns `0`, `"abcabcabc".lastIndexOf('a')` returns `6`. If the string does not contain character `c` after the start index, then a special value of `-1` will be returned, e.g., `"abcabcabc".lastIndexOf('a', 7)` returns `-1`.

#### 1.5.7 `str1.contains(str2)`

`str1.contains(str2)` returns `true` if `str1` contains `str2`, else `false`, e.g.: `"hello".contains("ll")` returns `true`, `"hello".contains("ho")` returns `false`.

#### 1.5.8 `str.substring(startIdx)`

`str.substring(startIdx)` returns a substring of `str`, which starts at index `startIdx` until the end of the string. The character at `startIdx` is included, e.g., `"hello".substring(3)` returns `"lo"`. If the given index is too big, an `index out of bound exception` will be thrown, e.g.: `"hello".substring(5)`.

#### 1.5.9 `str.substring(startIdx, endIdx)`

`str.substring(startIdx, endIdx)` returns a substring of `str`, which starts at index `startIdx` and ends at `endIdx`. The character at `startIdx` is included, while the character at `endIdx` is excluded, e.g., `"hello".substring(1, 3)`returns `"el"`. If the given index is too big, an `index out of bound exception` will be thrown, e.g.: `"hello".substring(2, 5)`.

#### 1.5.10 `str.toUpperCase()`

`str.toUpperCase()` returns a string that has the context as `str` but all letters are uppercase, while numbers and symbols remain the same, e.g.: `"Hello123!".toUpperCase()` returns `"HELLO123!"`. Note that `str.toUpperCase()` does not affect the original string, write `str = str.toUpperCase()` to update the original string.

#### 1.5.11 `str.toLowerCase()`

`str.toLowerCase()` returns a string that has the context as `str` but all letters are lowercase, while numbers and symbols remain the same, e.g.: `"Hello123!".toLowerCase()` returns `"hello123!"`. Note that `str.toLowerCase()` does not affect the original string, write `str = str.toLowerCase()` to update the original string.

#### 1.5.12 `str.strip()`

`str.strip()` returns a string that has the context as `str` except all white spaces at the beginning and at the end of the string, e.g.: `"   hello    ".strip()` returns `"hello"`.

#### 1.5.13 `str.isEmpty()`

`str.isEmpty()` returns true if `str` is empty, else `false`, e.g.: `"".isEmpty()` returns `true`, `"Hello123!".isEmpty()`returns `false`.

#### 1.5.14 `str.isBlank()`

`str.isBlank()` returns true if `str` is empty or if it contains white space only, else `false`, e.g.: `"".isBlank()` returns `true`, `"   ".isBlank()` returns `true`, `"Hello123!".isBlank()` returns `false`.

#### 1.5.15 `str1.equals(str2)`

`str1.equals(str2)` returns true if the context of  `str1` is the same as the context of `str2`, else `false`, e.g.: `"hello".equals("hello")` returns `true` , `"hello".equals("HELLO")`returns `false`.

#### 1.5.14 `str1.equalsIgnoreCase(str2)`

`str1.equalsIgnoreCase(str2)` is very similar to `str1.equals(str2)`, but case-insensitive, e.g.: `"hello".equals("hello")` returns `true` , `"hello".equals("HELLO")` also returns `true`.

#### 1.5.16 `String.valueOf(value)`

`String.valueOf(value)` generates a string with the value of `value`, e.g.: `String.valueOf(123)`returns `"123"`, `String.valueOf(true)`returns `"true"`.

#### 1.5.17 `String.format(pattern, fulfill values)`

`String.format(pattern, fulfill values)` is very similar to `printf()`, but instead of printing the value, it returns a string, e.g.: `String str = String.format("Total price: %.2f", totalPrice);`, then `str` equals `"Total price: 4.57"`.

## 2. Console Input

Previously, we learned how to use `print()`, `println()`, and `printf()` to display output on the console. We can also read input from the console using the `Scanner` class.

The syntax is

```java
Scanner console = new Scanner(System.in);

// input an int
int num1 = console.nextInt();       

// input a double
doyble num2 = console.nextDouble();

// input a String 
String str1 = console.next();       // extract the input by both space and enter
String str2 = console.nextLine();   // extract the input by only enter
```

Example:

```java
Scanner console = new Console(System.in);

// age should be an int, user enter 17 and enter
System.out.print("Please enter your age: ");
int age = console.nextInt();        

// name should be a String, and since name may contain spaces, we should use nextLine() instead of next() or the input will be extracted when it reaches the first space.
System.out.print("Please enter your name: ");       
String name = console.nextLine();       // user input Yi Wang, and name equals Yi Wang
String name = console.next();           // user input Yi Wang, but name equals Yi

// gender should also be a String, but since it does not contain a space, we can use next().
System.out.print("Please enter your gender: ");
String gender = console.next();   
```

You can also input multiple values at once:

```java
Scanner console = new Console(System.in);

// if user inputs "3 5", then 3 will be stored in num1 and 5 will be stored in num2
System.out.print("Please enter two numbers: ");
int num1 = console.nextInt();   
int num2 = console.nextInt();   
```

Note: If the input cannot be converted to the expected type, `nextInt()` or `nextDouble()` will throw an `InputMismatchException`:

```java
// nextInt() will cause an exception
System.out.print("Please enter your age: ");
int age = console.nextInt();                    // user input "3.14" 

// nextDouble() will cause an exception
System.out.print("Please enter a number: ");
double num = console.nextDouble();              // user input "hello" 
```
