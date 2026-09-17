## Class 4 Sep 2 2026

- Each primitive data type has a corresponding *wrapper class*, e.g., `int` -> `Integer`, `double` -> `Double`, and `boolean` -> `Boolean`. We will see these classes in the future.
- Java will default every number as an `int`, if one wants a `long` number, end the number with `L`, if float then end the number with `f`
- `Interger.MAX_VALUE` gives the maximal interger limit (2147483647). `Interger.MIN_VALUE` gives the minimal interger limit (-2147483648)(Constant). E.g.
    ```java
    int num = Interger.MAX_VALUE
    ``` 
    This can be used with other types of classes like `short`, `long`, `double`, `float` and `char`.
- `Double.POSITIVE_INFINITY` and `Double.NEGATIVE_INFINITY` are special Double cases(Constant).
    | Value                        | Meaning                             | Example                                    |
    | ---------------------------- | ----------------------------------- | ------------------------------------------ |
    | `Double.MIN_VALUE`         | the minimum positive value a `double` can reach | `double num = Double.MIN_VALUE;`         |
    | `Double.MAX_VALUE`         | the maximum a `double` can reach   | `double num = Double.MAX_VALUE;`         |
    | `Double.POSITIVE_INFINITY` | positive infinity                   | `double num = Double.POSITIVE_INFINITY;` |
    | `Double.NEGATIVE_INFINITY` | negative infinity                   | `double num = Double.NEGATIVE_INFINITY;` |
    | `Double.NaN`               | not a Number                        | `double num = Double.NaN;`               |
- If the first letter is **CAPITALIZED**, it is a **CLASS**
- Once a method is finished, all of the variables in that method will be erased from memory
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
- Java doesn't like it when we put a single quote in between a pair of single quotes, computer understands only the first and second single quote, same story with double quotes
    
    ```java
    String str = ''';
    String str1 = """;
    
    //This is wrong
    ```

    - Use an escape sequence instead (back slash `\`).
    
    ```java
    String str = '\'';
    String str1 ="\"";
    ```

     - This whole thing wil print `'` and `"`
    - `/n` will print an enter key
    ```java
    String str = "hello. \nhello. \nhow are you? \ngood good";
    /* Will print
    hello.
    hello.
    how are you?
    good good
    */
    ```
    - `/t` is for tab
    ```java
    String str = "a\tb\tc";
    String str1 = "aa\tbb\tcc";
    /* Will print
    a	b	c
    aa	bb	cc 
    */
    ```
    - If we want to write a path to a file or a directory, we have to use `\\`
    ```java
    String path = "C:\Users\2608037\Downloads"
    //This is wrong
    
    String path2 = "C:\\Users\\2608037\\Downloads"
    // This is better
    ```
    - Summary

    | Combination | To Represent |
    | ----------- | ------------ |
    | `\n`      | `enter`    |
    | `\t`      | `tab`      |
    | `\"`      | `"`        |
    | `\'`      | `'`        |
    | `\\`      | `\`        |
- Always keep code clean
    - Names of variables has to be self documentary
    - Add spaces around each keyword, after comma and around operators that operate on two values.
    ```java
    int num1 = 5;   // clean
    int    num1 = 5;   // unclean
    int num1=5;   // unclean
    int num1 =5;    // unclean
    int num1 = 5 ;   // unclean
    ```
    - Add empty lines to group code into a catagories
    
    ```java
    double num1 = 5;
    double num2 = 10;
    double num3 = 15;

    double sum = num1 + num2 + num3;
    double avg = sum / 3;

    System.out.println("The sum is " + sum);
    System.out.println("The average is " + avg);
    ```

    - Do not do this
    
    ```java
    double num1 = 5;

    double num2 = 10;

    double num3 = 15;

    double sum = num1 + num2 + num3;

    double avg = sum / 3;

    System.out.println("The sum is " + sum);

    System.out.println("The average is " + avg);
    ```

    - Avoid using magic numbers
- Arithmetic Calculation
    1. `+`: Addition
    2. `-`: Subtraction
    3. `*`: Multiplication
    4. `/`: Division
    5. `%`: Modulo
- Normal division will always throw away the decimal part of the number, so `10 / 3` is going to be `3` when it's supposed to be 3.3333..., `9 / 10` will be `0`
- So, `interger` / `interger` = `interger`. If an `interger` does an operation with a `double`, then the result will be a `double`. `2 + 1.1` will be `3.1`
    ```java
    System.out.println(10 / 3);
    // Will print out 3
    System.out.println(10.0 / 3);
    // Will print out 3.3333333333
    System.out.println(1 + 2.1);
    // Will print out 3.1
    ```
- Auto-conversion means if we do this
    ```java
    long num = 3;
    // Java will convert 3 to 3L
    // It will auto convert when it's safe
    ```
    This also works with int -> double
- Modulo ( % ) results the part that remains after a division
    ```java
    System.out.println(10 % 3);
    // Will print out 1
    System.out.println(6 & 13);
    // Will print out 6
    System.out.println(13 & 6);
    // Will print out 1
    ```
