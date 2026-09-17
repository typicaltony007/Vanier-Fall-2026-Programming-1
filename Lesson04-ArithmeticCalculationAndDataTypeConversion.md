# Lesson04-ArithmeticCalculationAndDataTypeConversion

### Table of Contents

- [1. Arithmetic Calculation](#1-arithmetic-calculation)
  - [1.1 Division](#11-division)
  - [1.2 Modulo](#12-modulo)
  - [1.3 Assign Operation](#13-assign-operation)
  - [1.4 Shorthand Operations](#shorthand-operation)
  - [1.5 Priority](#15-priority)
- [2. Data Type Conversion](#2-data-type-conversion)
- [3. Keep Code Clean 3](#3-keep-code-clean-3)

## 1. Arithmetic Calculation

Java provides five fundamental arithmetic operators:

1. `+`: Addition
2. `-`: Subtraction
3. `*`: Multiplication
4. `/`: Division
5. `%`: Modulo

The first three operations are straightforward. However, division may behave slightly differently from what you have encountered previously, and the modulo operation introduces a new concept.

```java
int num1 = 1 + 2;
int num2 = 3 - 1;
double num3 = 1.2 * 3.4;
```

### 1.1 Division

When an integer is divided by another integer, the result is also an integer. For example, 10 / 2 equals 5. If the division produces a fractional part, it is discarded regardless of its value. For instance:
- `10 / 3` equals 3
- `10 / 4` equals 2
- `9 / 10` equals 0

Dividing an integer by 0 will result in a `divide by zero` exception.

### 1.2 Modulo

The **modulo** operation, often abbreviated as **mod**, calculates the remainder after division. For example, to compute `10 % 3`, the division `10 / 3` is first performed, which gives 3 as the quotient, leaving a remainder of 1.

A way to understand `a % b` is to imagine having $a in your pocket and purchasing as many items as possible, each costing $b. The result of the modulo operation represents the amount of money left.

For example, `10 % 3` can be interpreted as having $10 and buying items worth $3 each. You can buy 3 items for $9, leaving $1 remaining. Therefore, 10 % 3 equals 1.

There are two special cases to note:
1.	Any positive integer modulo 1 equals 0 (e.g., `10 % 1 = 0`).
2.	A smaller integer modulo a larger integer equals the smaller integer itself (e.g., `3 % 10 = 3`).

In general, for `a % b`, the result is always in the range `[0, b)` (`[` and `]` includes the number, while `(` and `)` excludes the number). For example, `a % 3` can only produce 0, 1, or 2, regardless of the value of `a`.

One common application of the modulo operation is to determine whether a number is even or odd. If num is even, then `num % 2 = 0`; otherwise, `num % 2 = 1`.

### 1.3 Assign Operation

The `=` symbol represents an assignment operation. It assigns the value on the right-hand side to the variable on the left-hand side.

### Shorthand Operation

#### 1.4.1 `+=` Operation

In many situations, it is necessary to read the current value of a variable and then update it. For example, if your account balance is 10 and you withdraw 3, the new balance becomes 7. This can be implemented with the following code:

``` java
balance = balance - 3;
```

In this statement, the subtraction `-` is performed before the assignment `=`, meaning the original value of balance is read, the calculation is performed, and the result is then assigned back to `balance`.

Java also provides a more concise way to perform this type of operation.

1. `a += b;` can be used to represent `a = a + b;`
2. `a -= b;` can be used to represent `a = a - b;`
3. `a *= b;` can be used to represent `a = a * b;`
4. `a /= b;` can be used to represent `a = a / b;`
5. `a %= b;` can be used to represent `a = a % b;`

#### 1.4.2 `++` Operation

In certain situations, the value being added or subtracted is 1. For example, if you are counting the number of people entering a museum, you would increment a counter by 1 each time someone enters. This can be written as:

``` java
counter += 1;
```

Java provides an even more concise way to perform this operation:
1.	`a++;` or `++a;` is equivalent to `a = a + 1;` or `a += 1;`.
2.	`a--;` or `--a;` is equivalent to `a = a - 1;` or `a -= 1;`.

Note that Java does not support the operators `**`, `//`, or `%%`.

##### 1.4.2.1 Prefix or Postfix

When a statement contains only the `++` or `--` operation, the position of the operator does not affect the result. For example, `++a;` and `a++;` are equivalent.

However, if the statement involves other operations in addition to `++` or `--`, the position of the operator becomes significant:
- When `++` or `--` is placed before a variable (prefix), the operation is executed first.
- When `++` or `--` is placed after a variable (postfix), the operation is executed last.
  
```java
// there is no difference between num++ and ++num if the statement contains only ++
int num = 5;
num++;
++num;

// ++ is in front of num1, so ++ is first calculated before printting. 
int num1 = 5;
System.out.print(++num1);     // print 6

// ++ is after num1, so ++ is last calculated after printting. 
int num2 = 5;
System.out.print(++num2);     // print 5, then num2 = 6
```

### 1.5 Priority

In Java, the operators `*`, `/`, and `%` have higher precedence than `+` and `-`, while the assignment operator `=` has the lowest precedence.

Parentheses `()` can be used to explicitly alter the default precedence and control the order of operations.

```java
int num1 = 1 + 2;   // first execute 1 + 2, then execute num = 3, no need to change the priority
int num2 = 1 + 2 * 3;  // first execute 2 * 3, then execute 1 + 6, then execute num2 = 7
int num3 = (1 + 2) * 3;  // first execute 1 + 2, then execute 3 * 3, then execute num3 = 9
```

## 2. Data Type Conversion

In previous examples, we only considered operations between `int` and `double` values. In practice, values of different data types can interact in calculations.

The general rule in Java is that it does not directly perform operations on values of differing data types. Instead, Java attempts to safely convert the values to a common data type before performing the calculation. This process is called auto-conversion.

### 2.1 Auto-conversion

A conversion is considered safe if Java can convert a value from one type to another without losing any data. For example, converting the integer 3 to a `double` results in 3.0, which is safe because no information is lost.

Conversely, converting a `double` value such as 3.1 to an `int` is not safe, because the fractional part is discarded and the value becomes 3. This is called a **lossy conversion**.

Common conversions and their safety are summarized in the following table:

| From   | To     | IsSafe |
| ------ | ------ | ------ |
| int    | double | True   |
| double | int    | False  |
| float  | double | True   |
| double | float  | False  |
| int    | char   | True   |
| char   | int    | True   |
| Any    | String | True   |

The conversion to `String` will be explained later when we study the `String` class.

This table explains why it is possible to assign an integer value to a `double` or `char` variable: Java can safely convert an integer to these types.

```java
// Correct
double num = 3;   // Java converts 3 into 3.0, and then assign it to num
char character = 97;  // Java convert 97 to 'a' and then assign it the character

// Wrong
int num1 = 3.14;  // Java cannot convert a double to an int safely
float num2 = 3.14;  // Java cannot convert a double to a float safely
```

When Java evaluates an expression like `10 / 4.0`, it first checks whether the operands can be safely converted to the same data type. Since an int can be safely converted to a double, Java converts 10 to 10.0 and then performs the division as a double operation. The result is also a double:

```
10 / 4.0 -> 10.0 / 4.0 -> 2.5
```

Another example is:

``` java
char character = 'a' + 1;
```

Here, the expression involves two operations: `+` and `=`. Since `+` has higher precedence than `=`, Java first evaluates `'a' + 1`. In this operation, a `char` is added to an `int`. Java converts the `char` `'a'` to its integer value 97, performs the addition, and produces an int result:

```
'a' + 1 -> 97 + 1 -> 98
```

Java then assigns this int value to the char variable character, safely converting 98 back to the corresponding char `'b'`:

```
char character = 'a' + 1 -> char character = 97 + 1 -> char character = 98 -> char character = 'b';
```

### 2.2 Manual-conversion

In some situations, we may want to convert a value to another data type unsafely. For example, if a timer stores a real-time value as a `double`, such as 5.86, but we only want to use the integer part 5, we need to convert the `double` to an `int` and discard the fractional part.

Even though this is the desired behavior, Java will not perform this conversion automatically because it is considered unsafe. To enforce such a conversion, we must explicitly cast the value.

**Manual type conversion**, or **casting**, is performed by placing the target type in parentheses immediately before the value.

```java
int num1 = (int) 3.14;   // Java first convert 3.14 to 3, then assign 3 to num1
float num2 = (float) 3.14; // Java first convert 3.14 to 3.14f, then assign 3.14f to num2
```

Manual conversion, or casting, is also considered an operation. Its precedence is **higher than that of all arithmetic operations**, so care must be taken when combining it with other operators.

```java
System.out.print((char) 'a' + 1);  // print 98, Java will first execute manual-conversion, then +, thus the manual-conversion does not affect anything
System.out.print((char) ('a' + 1));  // print 'b', Java will first execute +, then manual-conversion, thus the manual-conversion affect the result
```

Note that the `boolean` type cannot be converted to any other primitive data type.

## 3. Keep Code Clean 3

1. A whitespace should be added after the manual-conversion target data type:

   ```java
   (int)3.14   // unclean
   (int) 3.14  // clean
   ```

2. Parentheses `()` should only be used to change the order of operations when necessary:

   ``` java
   int num1 = (1 + 2);   // unclean
   int num2 = 1 + 2;     // clean
   int num3 = (1 + 2) * 3;   // clean
   ```

3. Prefer concise operators when possible:
- Use `a++` or `++a` instead of `a += 1`.
- Use `a += b` instead of `a = a + b`.

4. Do not add spaces before the parentheses `()` when defining or calling a method.

``` java
public static void main(String[] args) {
   // calling a method
   System.out.println ("Hello World"); // unclean
   System.out.println("Hello World");  // clean
}

// defining a method
public static void anotherMethod1 () {  // unclean

}

public static void anotherMethod2() {  // clean

}
```
