# Lesson05-Math Class and Random Class

### Table of Contents

- [1. Math Class](#1-math-class)
- [2. Random Class](#2-random-class)
  - [2.1 `import` statement](#21-import-statement)
  - [2.2 Random Strategy](#22-random-strategy)

## 1. Math Class

In addition to arithmetic operators, the JDK offers the `Math` class for common mathematical calculations.

| Method           | Usage                                        | Example                          | Result               |
| ---------------- | -------------------------------------------- | -------------------------------- | -------------------- |
| `Math.pow(a, b)` | calculates the `a` power of `b`              | `double num = Math.pow(2, 3);`   | `8`                  |
| `Math.sqrt(a)`   | calculates the square root of `a`            | `double num = Math.sqrt(4);`     | `2`                  |
| `Math.min(a, b)` | gets the smaller value between `a` and `b`   | `double num = Math.min(2, 3);`   | `2`                  |
| `Math.max(a, b)` | gets the bigger value between `a` and `b`    | `double num = Math.max(2, 3);`   | `3`                  |
| `Math.round(a)`  | rounds `a` either up or down                 | `double num = Math.round(3.14);` | `3.0`                |
| `Math.ceil(a)`   | rounds `a` up                                | `double num = Math.ceil(3.14);`  | `4.0`                |
| `Math.floor(a)`  | rounds `a` down                              | `double num = Math.floor(3.14);` | `3.0`                |
| `Math.abs(a)`    | gets the absolute value of `a`               | `double num = Math.abs(-2);`     | `2`                  |
| `Math.random()`  | generates a random number in range `[0, 1)`  | `double num = Math.random();`    | `0.8200578291667548` |
| `Math.sin(a)`  | calcualtes the sin value of angle (in radians) `a` | `Math.sin(30 * Math.PI / 180);`  | `0.499999` |
| `Math.cos(a)`  | calcualtes the cos value of angle (in radians) `a` | `Math.cos(60 * Math.PI / 180);`  | `0.5` |
| `Math.toRadians(a)`  | convert an angel from degrees to radians | `Math.sin(Math.toRadians(30));`  | `0.499999` |

1.	`Math.pow(a, b)` – This method is used for exponentiation. For example, if your salary increases by 5% each year, and the initial salary is salary, then:
- After 1 year: `salary * (1 + 0.05)`
- After 2 years: `salary * (1 + 0.05) * (1 + 0.05) = salary * Math.pow(1 + 0.05, 2)`
- In general, after year years: `salary * Math.pow(1 + 0.05, year)`
2.	`Math.sqrt(a)` – This method returns the square root of a number. For example, it can be used in the formula for calculating the standard deviation, which involves square root operations.
3.	`Math.ceil(a)` – This method always rounds a number up to the nearest integer. A common example is parking fees: if you park your car for 1 hour and 10 minutes, you are often charged for 2 full hours. In this case, Math.ceil ensures that the number of hours is rounded up.

the `Math` class also contains constants such as: 

| Constant  | Usage           |
| --------- | --------------- |
| `Math.PI` | the value of Pi |
| `Math.E`  | the value of e  |

## 2. Random Class

If we need a random number in the range `[0, 1)` (`[` means included, `)` means excluded), we can directly use `Math.random()`.

However, when we need numbers in other ranges, especially integers, `Math.random()` becomes less convenient. In such cases, it’s better to use the Random class from the java.util package.

For example, suppose we want to simulate rolling a dice, which should generate a random integer in the range `[1, 6]` (or equivalently `[1, 7)`). We can do this as follows:

```java
Random rand = new Random();
int dice = rand.nextInt(1, 7);  // 1 is included, and 7 is excluded
// or 
int dice = rand.nextInt(6) + 1; // [0, 6) + 1
```

### 2.1 `import` statement

When you type `Random`, IntelliJ will pop up an auto-complete menu, and the first element is `Random   java.util`, press enter to choose it, this will allow IntelliJ to automatically import the class for you, and you will see a line of code added at the very beginning of your file.

```java
import java.util.Random;  // this line is automatically generated

Random rand = new Random();
int dice = rand.nextInt(1, 7);
```

This is the first time we see the `import` statement, so let’s take a closer look at what it does.

When you install the JDK, a huge number of classes are installed on your computer. These classes are tools you can use in your programs. Some of them are very popular and used all the time, while others are less common.

Whenever you start programming, Java will automatically bring in some of the most frequently used tools into your environment. For example, `System.out.println()`, `System.out.print()`, and the `Math` class are always available without you needing to do anything.

But for other tools that are less frequently used, such as `Random`, Java requires you to explicitly tell it to bring them in. That’s why we write `import java.util.Random;`

### 2.2 Random Strategy

Computers cannot truly understand or generate real randomness. What Java gives us is actually a pseudo-random number — it looks random, but is actually calculated.

The idea is this:
- There is a complicated mathematical formula `f(x)`.
- It takes an input value, called a **seed**, and produces a result.
- Because the formula is so complex, the result looks very different from the seed.

If we keep using the result (or a new seed) as input to the formula, and then map the result into the required range, we get a sequence of numbers that appear random.

Many programming languages use the current time (in seconds, milliseconds, or nanoseconds) as the seed, so the numbers change each time you run the program.

For example, suppose we want to generate a dice roll in the range `[1, 7)`. If the seed is 0, then `f(0)` might give 1029417. Java then takes that result and calculates:

``` java
1029417 % 6 = 3
```

Here, `% 6` ensures the result is in the range `[0, 6)`. But since dice numbers should be `[1, 7)`, we simply add 1.

So in this case, the final dice value is 3 + 1 = 4.
