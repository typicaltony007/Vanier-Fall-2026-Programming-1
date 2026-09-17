## Class 5 Sep 9 2026

- Modulo
    ```
    a % b = [0, b-1]
    
    ```
- Safe auto-conversion 
    - int -> double
    - float -> double
    - int <-> char
        ```java
        System.out.println((char)('a' + 1)); 
        //auto-converts int-> char after doing the operation
        //the order doesn't matter, java will bring both to the same data type
        ```
- Unsafe manual conversion
    - double -> int
        ```java
        //you have to manually convert
        int num2 = (int) 3.14;
        //syntax: var_type var_name = (var_type) var_value;
        double num = (double) 3;
        //correct but redundant, counts as a minor mistake
        ```
- int to str
    ```java
    System.out.println("1 + 2 = " + 1 + 2); 
    //java will convert everything to str before adding them
    //the result will be "1 + 2 = 12"
    ```
    ```java
    System.out.println(1 + 2 + " = 1 + 2"); 
    //java will convert everything to str after, when it gets there, order is important
    //the result will be "3 = 1 + 2"
    ```
    ```java
    System.out.println("1 + 2 = " + (1 + 2));
    //java will work inside the parenthesis before doing the big addition opperation
    //the result will be "1 + 2 = 3"
    ```
- Java has tool boxes - Math Class and Random Class
- Syntax
    ```java
    tool_box.method()
    // for example
    System.out.println()
    ```
- IMPORTANT NOTE: class always has the first letter capitalized, methods dont have capitalized letters
- For anything that has to do with mathematical opperations, use the `Math` class
    - `Math.pow(a, b)` does a to the b power, both a and b will be converted to double, and the result will be double
    - `Math.sqrt(a)` does the square root of a, the result will be double
    - `Math.min(a, b)` it selects the smallest value in the set, a and b can be int, float, long or double, `.max` will do the opposite
        - If we want to to compare more values, we have to nest more `Math.min`
        ```java
        Math.min(Math.min(num1,num2), num3)
        ```
    - `Math.round(a)` will round the number, if it's x.5, it will round up, if it's x.4, it will round down. If a is an float, result will be int, if it's a double (almost always is), the result will be a long
    - `Math.ceil(a)` round up the value, a will be auto converted into a double, the result will be a double, `.floor` will round down the value
        - Rounding up applications can be a parking meter.
        - Rounding down is to give a margin.
    - `Math.abs(a)` absolute value of a, a can be int long float and double
    - `Math.sin(a)` a will be converted to double, a WILL BE IN RADIANS
- Today's code
```java
package org.example;

public class Main {
    static void main() {
        double num = 5;     //auto-conversion int -> double
        char c = 97;        //auto-conversion int -> char
        System.out.println("hello " + 123);     //auto-conversion int -> str
        System.out.println("hello " + 1.23);     //auto-conversion double -> str
        System.out.println("hello " + 'a');     //auto-conversion char -> str
        /*
        printed out result:
        hello 123
        hello 1.23
        hello a
         */
        int num2 = (int) 3.14;
        System.out.println('a' + 1); //auto-converts char -> int amd then does the operation, want to print 'b'
        System.out.println((char)('a' + 1)); //auto-converts int-> char after doing the operation
        //the order doesn't matter, java will bring both to the same data type
        System.out.println("1 + 2 = " + 1 + 2); //java will convert everything to str before adding them if the first value is a string
        //the result will be "1 + 2 = 12"
        System.out.println(1 + 2 + " = 1 + 2"); //java will convert everything to str after, when it gets there, order is important
        System.out.println("1 + 2 = " + (1 + 2));
        System.out.println(Math.pow(2, 3));
        System.out.println(Math.sqrt(2));
        System.out.println(Math.min(2, 1));
        System.out.println(Math.sin(Math.toRadians(30)));
    }
}
```
