## Class 3 Aug 31 2026

- Press `shift + f10` to run code
- `package` is a bag for organizing
- `class` is an object that can contain methods
- Java is OOP obligated: everything must be defined in a class
- `/** aaaa **/` is called javadoc, java documentation. It has a standard way to write it
- `ctrl + /` to comment entire lines
- `shift + up arrow` to select lines
- To modify many lines of code, one needs to first copy a section of code (1), then comment it using `//` (2), and then proceed to modify the code (3)
- `{}` is like a bag, something belonging to the fuction 
- Need to indent one level (press `tab`) when adding any new code inside the brackets `{}`. One `tab` is equal to 4 spaces

- `Main` is a special class, but `main` is not a class nor a project, it's a special method. The `Main class` alwats contain a `main()` method
- A method is a piece of code to do some task (90% the name is a verb)
- A method is always follow by a pair of parenthesis `()`, e.g.: `main()`, `println()`
- A project can have many classes
- A class can contain many methods
- In Java, every project starts at the `main()` method
- There should be only one `main()` method in an entire project
- `System.out.println()` to print a line, shortcut is `sout`
- `System.out.print()` to print a string in the same line, e.g.
     ```java
     System.out.print(a);
     System.out.print(b);
     ```
    This should print `ab`
- Statements ends with `;`
- `static void main ()` shortcut is `psvm`, because the full method is called `public static void main()`
- Variables in Java needs a type and a name, in the example below `int` is a type and `num` is a name and `5` is an int
    ```java
    int num = 5
    ``` 
- There are 8 different types of variables (5 interger, 2 floating and 1 boolean)
- Interger (number without dot): 
    - `byte` : it allows 8 bits, 7 bits are used to describle a number, the last one is used for the sign (positivie/negative), the biggest number it can go to is 127 (0111 1111), the smallest number it can go to is - 128 (1111 1111)
    - `short` : it allows 16 bits (2 bytes), max is 2^15 and min is -(2^15)
    - `char` : stands for characters
        - Has 2 types: Unicode - big dictionary and ASCII - small dictionary (American Standard Code for International Interchange)
        - Single quote `''` is for a single character, `""` is a **string**
        - Syntax is 
        ```java
        char letter = 'a';
        ```
        - `char` allows 2 bytes
    - `int` : it allows 32 bits (4 bytes), max is 2^31 and min is -(2^31)
    - `long` : it allows 64 bits (8 bytes), max is 2^63 and min is -(2^63)
- Floating (numbers with a dot):
    - `float` : takes 4 bytes
    - `double` : takes 8 bytes
- Boolean (true or false) : 
    - `boolean` : True or False
- The most frequently used ones are: `char`, `int`, `double`, and `boolean`
- When a variable is made, one needs to declare it and initialize it immediately, or declare a variable and initialize it later
    ```java
    int num = 3 // declare a variable and initialize it
    ```
    Or
    ```java
    int num2    // declare a variable
    num2 = 5    // initialize it
    num2 = 3    // the value 5 is over-written by 3, so after this line, num2 means 3
    ```
- Variables' names should be self documented (it should describle/explain itself), it should be typed in camel case, with the first letter being lowercase
- To rename a variable, select the variable (1) and then press `shift + f6` (2) and then rename it (3). It should rename every variable with the same name
- Code made today
    ```java
    package org.example;

    public class Main {
        static void main() {
            double originalPrice = 3.99;
            double taxRate = 0.15;
            double tax = originalPrice * taxRate;
            double taxedPrice = originalPrice + tax;
            double tipRate = 0.15;
            double tip = originalPrice * tipRate;
            double finalPrice = tip + taxedPrice;
            System.out.println(finalPrice);
        }
    }
    ```
