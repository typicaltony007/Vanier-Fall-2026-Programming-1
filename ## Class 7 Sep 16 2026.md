## Class 7 Sep 16 2026
- Only `String.valueOf` and `String.format` are the only methods that are called through the class
- `String.valueOf` converts a data type to a string
- Index range starts at [0, length - 1]
    - E.G.
    ```
    hello
    01234
    idx = 1 e
    idx = 4 o
    idx = 5 idxOutOfBound
    idx = -1 idxOutOfBound
    ```
- Length is normal counting like `1 2 3 4 5`
- Index is counting -1, starts at 0 like `0 1 2 3 4`
- `str.length()`        returns the length of the string
- `str.charAt(idx)`     idx = char
- `str.indexOf(char)`   char = idx  
    - only returns first appearance
    - if we search for a character that does not exist in the string, it returns -1
    - str = idx (smallest value first appearance)
- `str.indexOf(char/string, fromIndex)`  searches starting at fromIndex
- `str.indexOf(char/string, beginIndex, endIndex)`   [beginIndex, endIndex)
- `str.lastIndexOf(char/string, beginIndex, endIndex)`
- `str.contains(string)`    
    - returns a boolean
    - case-sensitive
- `str.toLowercase()`       create a new string with all lowercase
- `str.toUppercase()`       create a new string with all uppercase
- `str.substring(startIndex)`           
    - create a new substring from the startIndex til the endOfString
- `str.substring(startIndex, endIndex)` 
    - create a new substring
- `str.isEmpty`     ""      is empty and blank
- `str.isBlank`     "   "   is blank but not empty
- `str.trim`   
    - returns a new string, without the heading and the ending spaces
    ```java
    String str = "   a b c   ";
    System.out.println(str.trim())
    // will return "a b c"
    ```
- `str.equals(str2)` boolean    case-sensitive
    - Compares if both are the same
    - Application can be password verification
- `str.equalsIgnoreCase(str2)` boolean      case-insensitive
- SINGLE QUOTE FOR SINGLE CHARACTER, DOUBLE QUOTE FOR STRING
- Today's code
```java
package org.example;

import java.util.Random;

public class Main {
    static void main() {
        Random random = new Random();
        int num = random.nextInt(0, 20);
        System.out.println(num);
        String str = "hello world afwufggfgfgqfgqwfg";
        System.out.println(str.charAt(num));
        /*
        str.length()        returns the length of the string
        str.charAt(idx)     idx = char
        str.indexOf(char)   char = idx  only returns first appearance
        str.indexOf(char, fromIndex)
        str.indexOf(char, beginIndex, endIndex)
        str.contains(string)    returns a boolean   case-sensitive
        str.toUppercase()       create a new string with all uppercase
        str.toLowercase()       create a new string with all lowercase
        str.substring(startIndex, endIndex) create a new substring
        str.substring(startIndex)           create a new substring from the startIndex til the endOfString
         */
        System.out.println(str.indexOf("ll"));
        int num2 = str.indexOf('l', 10);
        System.out.println(str.contains("H"));
        System.out.println(str.toUpperCase());
        System.out.println(str);
        str = str.toUpperCase();
        System.out.println(str);
        System.out.println(str.substring(2, 4));

        String email = "Mike@google.com";
        email = email.toLowerCase().trim();
        int atIdx = email.indexOf('@');
        String account = email.substring(0, atIdx);
        System.out.println(account);
    }
}
```
