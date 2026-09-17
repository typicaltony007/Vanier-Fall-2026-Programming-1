## Class 6 Sep 14 2026
- To get Pi and Euler's number:
    ```java
    double pi = Math.PI;
    System.out.println(pi);
    double e = Math.E;
    System.out.println(e);
    /* Prints out
    3.141592653589793
    2.718281828459045
    */
    ```
- Assign operatior `=` is the lowest priority operator
- Manual conversion is the highest priority operator. E.g. (int), (double), etc
- How to get a variable that references itself in the calculation
    ```java
    double balance = 100;
    balance = balance * (1 + interestRate);
    //balance *= 1 + interestRate
    ```
    You can do `+=`, `-=`, `*=`, `/=`, and `%=`
- `++` increases the same number by 1 and `--` decreases the number by 1
    ```java
    int a = 5;
    a++ //The ++ is next to the a because you only need a space if there's a value on the left and the right of the operator
    // a will be 6 now
    ```
    ```java
    int a = 5;
    System.out.println(++a); //a will print 6 (update first and then print)
    System.out.println(a++); //a will print 5 (print first and then update)
    //if ++ goes first, java update first, if ++ goes after, it will update after, same with --
    ```
    If `++` and `--` is isolated, then the order does not matter
    ```java
    int b = a++ + 1; //java will print out 6 because the ++ is after the a
    System.out.println(a);
    System.out.println(b);
    //java will print out 
    //6
    //6
    int b = ++a + 1; //java will print out 7 because the ++ is before the a
    System.out.println(a);
    System.out.println(b);
    //java will print out 
    //6
    //7
    //++ or -- combined with another operation
        //++a : update first, other operations later
        //a++ : other operations first, update later
    ```
- `import` statement, when we use a different toolbox like `Random`, you need a line like `import java.util.Random;` at the start. IntelliJ will auto add that line.
- Orange is KEYWORD
- To use any tools that needs the *import line*, we have to type a line like this first
    ```java
    Random random = new Random();
    //Stuff stuff = new Stuff();
    //The pattern goes like that
    //Something something = new Something();
    Math.pow (a, b)
    //This calls the method through the class *Math*
    random.
    //This calls the method through the object (or variable) *random* 
    ```
- When we give a range in java, the first value will be included and the second value will be excluded
    ```java
    int dice = random.nextInt(0, 6);
    //java will print out a random number from 0 to 5
    int dice = random.nextInt(56);
    //java will print out a random number from 0 to 55
    int dice = random.nextInt();
    //java will print out a random number from int min to int max
    ```
- Seed is a value that you can put between the parenthesis of `Random random = new Random();`, the seed will produce the same value every time
    ```java
    Random r1 = new Random(1);
    Random r2 = new Random(1);
    System.out.println(r1.nextInt(100))
    System.out.println(r2.nextInt(100))
    //java will print out the same value for both
    ```
- Math: call method through class
- Random: call method through object
- String: call method through both class and (mainly) object
- A string is a **CLASS** (needs to be written with uppercase)
    ```java
    String str1 = "hello";
    ```
    ```java
        int num1; // data type is the template, the var contains the actual value
        int num2;
        String str1 = "hello"; // class is the template, the object contains the actual value
        String str2 = "world"; // context is contained in the object
    ```
- If the tool is based on context, you need to call it from the object
- If the tool is an operation, you need to call it from the class
- `"hello".length` will return 5, `.length` will return the length of the string
    ```java
    String str = "hello";
    int len = str.length();
    System.out.println(len);
    ```
- Index system [0, str.length()) or [0, str.length() - 1]
- Concatenation is to join 2 strings together, also to convert any type of data into a string
    ```java
    String str2 = "" + num;
    String str = String.valueOf(num)
    ```
- To convert a string to any other data type, we can do DataClass.parseDataClass
    ```java
    Interger.parseInt(str);
    Double.parseDouble(str);
    Boolean.parseBoolean(str);
    ```
- Today's code
```java
package org.example;

import java.util.Locale;
import java.util.Random;

public class Main {
    static void main() {
//        double pi = Math.PI;
//        System.out.println(pi);
//        double e = Math.E;
//        System.out.println(e);
//        int num = (int) 3.14 + 1;
//        System.out.println(num); //Prints out 4
//
//        //Balance example
//        double balance = 100;
//        System.out.println(balance);
//        balance = balance + 10;
//        System.out.println(balance);
//        balance = balance - 20;
//        System.out.println(balance);
//        double interestRate = 0.03;
//        balance = balance * (1 + interestRate); //balance *= 1 + interestRate
//        System.out.println(balance);
//
//        //Salary example
//        double salary = 70000;
//        double increaseRate = 0.05;
//        int year = 5;
//        salary = salary * Math.pow(1 + increaseRate, year);
//        System.out.println(salary);
//
//        //Mortgage example
//        double principle = 600000;
//        double interestRateMortgage = 0.04;
//        int yearMortgage = 30;
//        double total = principle * Math.pow(1 + interestRateMortgage, yearMortgage);
//        System.out.println(total);
//
//        //New example
//        balance += 10;
//        System.out.println(balance);
//
//        //++ and --
//        int a = 5;
//        a++;
//        System.out.println(a);
//
//        //++ or -- combined with another operation
//            //++a : update first, other operations later
//            //a++ : other operations first, update later
        Random random = new Random();
        int dice = random.nextInt(0, 6) + 1;
        System.out.println(dice);
        int num1; // data type is the template, the var contains the actual value
        int num2;
        String str1 = "hello world"; // class is the template, the object contains the actual value
        String str2 = "world"; // context is contained in the object
        String str3 = String.valueOf(5);
        // [0, str1.length());
        String str4 = "123";
        System.out.println(Integer.parseInt(str4) + 1);
    }
}
```
