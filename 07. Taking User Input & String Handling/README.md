# ***07. Taking User Input & String Handling***

## Table of Contents

1. [User input](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/07.%20Taking%20User%20Input%20%26%20String%20Handling#1-user-input)
2. [String Operations & Useful Functions](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/07.%20Taking%20User%20Input%20%26%20String%20Handling#2-string-operations--useful-functions)
3. [StringTokenizer (Splitting Text easily)](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/07.%20Taking%20User%20Input%20%26%20String%20Handling#3-stringtokenizer-splitting-text-easily)
4. [StringBuilder (For Modifying & Reversing Text))](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/07.%20Taking%20User%20Input%20%26%20String%20Handling#4-stringbuilder-for-modifying--reversing-text)
5. [Methods (Java's "Functions")](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/07.%20Taking%20User%20Input%20%26%20String%20Handling#5-methods-javas-functions)
6. [🧠 Mental Model](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/07.%20Taking%20User%20Input%20%26%20String%20Handling#-mental-model)
7. [📌 Key Terms to Remember](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/07.%20Taking%20User%20Input%20%26%20String%20Handling#-key-terms-to-remember)

---

## 1. User input

### A) The "Header" (`import` statement)

In **C**, you wrote `#include <stdio.h>` at the very top of your file to use functions like `printf()` and `scanf()`.

In **Java**, we use the `import` keyword:

Java

```java
import java.util.Scanner;
```

### What is `import`?

Java keeps its built-in tools organized inside folders called **Packages**.

- To save memory, Java doesn't load every tool automatically.
- By default, Java only loads basic things (like `System.out.println`).
- If you want to use the `Scanner` tool to take user input, you must tell Java where to find it: inside the `java.util` package.

### What else can you import?

Just like `#include`, you can import different packages for different tools:

- `import java.util.Random;` $\rightarrow$ To generate random numbers.
- `import java.util.Arrays;` $\rightarrow$ To perform operations on arrays.
- `import java.util.*;` $\rightarrow$ The  wildcard imports **all** tools inside the `java.util` package at once.

### B) Breaking Down the Scanner Line

Inside your `main` method, you create the input tool using this exact line:

Java

```java
Scanner sc = new Scanner(System.in);
```

Let's break down **every single word** in that line:

| **Word** | **What it means** | **Analogy / Explanation** |
| --- | --- | --- |
| **`Scanner`** | **Data Type / Class Name** | Tells Java what kind of tool we are creating (a Scanner tool). |
| **`sc`** | **Variable Name** | You can name this anything you want! (`input`, `scanner`, `sc`, `myInput`). |
| **`=`** | **Assignment Operator** | Connects the variable `sc` to the new Scanner object created on the right. |
| **`new`** | **Java Keyword** | Tells Java: *"Allocate fresh memory to create a new object."* |
| **`Scanner(...)`** | **Constructor** | Initializes the Scanner tool. |
| **`System.in`** | **Input Source** | Tells the Scanner to listen to your **keyboard** (standard input). |

### C) How to Read Different Types of Input

Once you write `Scanner sc = new Scanner(System.in);`, you can use `sc` to read whatever data type the user types in:

Java

```java
int age = sc.nextInt();         // Reads an integer number
double gpa = sc.nextDouble();   // Reads a decimal number
String word = sc.next();        // Reads a SINGLE word (stops at space)
String line = sc.nextLine();    // Reads a FULL sentence (reads until Enter is pressed)
```

### D) Simple Working Example

Here is a clean, 15-line program taking input for a student's profile:

Java

```java
import java.util.Scanner; // 1. Header import

public class StudentInput{
    public static void main(String[] args){

        // 2. Create the Scanner tool
        Scanner input = new Scanner(System.in);

        // 3. Ask for and read a single word
        System.out.print("Enter your name: ");
        String name = input.next();

        // 4. Ask for and read an integer
        System.out.print("Enter your age: ");
        int age = input.nextInt();

        // 5. Ask for and read a decimal number
        System.out.print("Enter your GPA: ");
        double gpa = input.nextDouble();

        // 6. Print the results
        System.out.println("\n--- Student Details ---");
        System.out.println("Name : " + name);
        System.out.println("Age  : " + age);
        System.out.println("GPA  : " + gpa);

        // 7. Close the scanner when done
        input.close();
    }
}
```

### Output:

Plaintext

```
Enter your name: Alex
Enter your age: 21
Enter your GPA: 3.85

--- Student Details ---
Name : Alex
Age  : 21
GPA  : 3.85
```

## **⚠️ The `nextInt()` + `nextLine()` Trap**

If you ask for a number (`nextInt()`) and then immediately ask for a full sentence (`nextLine()`), Java skips the text input!

### Why?

When you type `21` and hit **Enter**, `nextInt()` reads the `21`, but leaves the **Enter key action (`\n`)** behind. Then `nextLine()` sees that leftover **Enter** and thinks you pressed enter without typing anything!

### The Easy Fix:

Just add an extra `input.nextLine();` in between to clear that leftover Enter key:

Java

```java
System.out.print("Enter your age: ");
int age = input.nextInt();

input.nextLine(); // Clear the leftover Enter key!

System.out.print("Enter your full address: ");
String address = input.nextLine(); // Now works perfectly!
```

## 2. String Operations & Useful Functions

In Java, `String` comes with built-in "shortcut" functions that let you inspect, modify, and format text effortlessly.

### A) Most Commonly Used String Functions

Here are the most essential built-in String methods you will use every day:

| **Method** | **What it does** | **Simple Example** | **Output** |
| --- | --- | --- | --- |
| `length()` | Returns the total number of characters | `"Hello".length()` | `5` |
| `charAt(index)` | Gets the character at a specific position (starts at 0) | `"Java".charAt(1)` | `'a'` |
| `toLowerCase()` / `toUpperCase()` | Converts text to all lowercase or uppercase | `"Java".toUpperCase()` | `"JAVA"` |
| `trim()` | Removes extra spaces from the start and end | `"  hi  ".trim()` | `"hi"` |
| `substring(start, end)` | Cuts out a part of the text (end index is excluded) | `"Coding".substring(0, 4)` | `"Codi"` |
| `contains("text")` | Checks if a word/letter exists inside the string | `"Java".contains("av")` | `true` |
| `replace(old, new)` | Replaces characters or words with new ones | `"banana".replace("a", "o")` | `"bonono"` |
| `equalsIgnoreCase(text)` | Compares two strings ignoring capital/small letters | `"java".equalsIgnoreCase("JAVA")` | `true` |
| `split("delimiter")` | Cuts a string into an array based on a separator | `"A,B,C".split(",")` | `["A", "B", "C"]` |


### B) Comparing Strings: `equals()` vs `==`

> ⚠️ **Important Java Rule:** Never use `==` to compare two text strings!
> 
> - `==` checks if two strings share the **exact same memory location**.
> - `.equals()` checks if two strings contain the **same text characters**.

Java

```java
String s1 = "hello";
String s2 = new String("hello");

System.out.println(s1 == s2);      // false (Different memory locations!)
System.out.println(s1.equals(s2)); // true  (Same exact text content!)
```

## 3. StringTokenizer (Splitting Text easily)

If you have a long line of text separated by spaces, commas, or hyphens, `StringTokenizer` breaks it down into individual words (called **tokens**).

### Example:

Java

```java
import java.util.StringTokenizer;

public class TokenizerSimple{
    public static void main(String[] args){
        String data = "Apple,Banana,Mango,Orange";

        // Break text whenever a comma ',' is found
        StringTokenizer st = new StringTokenizer(data, ",");

        // Loop through and print each token
        while (st.hasMoreTokens()) {
            System.out.println(st.nextToken());
        }
    }
}
```

### Output:

Plaintext

```
Apple
Banana
Mango
Orange
```

## 4. `StringBuilder` (For Modifying & Reversing Text)

Standard Strings in Java cannot be altered once created. If you want to modify, append, or reverse a string easily, use `StringBuilder`:

Java

```java
public class StringBuilderSimple{
    public static void main(String[] args){
        StringBuilder sb = new StringBuilder("Hello");

        sb.append(" World"); // Adds text to the end -> "Hello World"
        sb.reverse();        // Reverses the text       -> "dlroW olleH"

        System.out.println(sb.toString());
    }
}
```

## 5. Methods (Java's "Functions")

In C, you defined functions outside `main()` and called them directly. In Java, functions are called **Methods**.

### A) Comparing C vs Java Functions

- **In C:**
    
    ```c
    int add(int a, int b){
        return a + b;
    }
    ```
    
- **In Java:**
    
    ```java
    public static int add(int a, int b){
        return a + b;
    }
    ```
    

### B) Line-by-Line Breakdown of a Java Helper Function

Java

```java
public static int calculateSum(int num1, int num2)
```

| **Word** | **What it means** |
| --- | --- |
| `public` | Access modifier (means this method can be accessed from anywhere in the project). |
| `static` | **Crucial keyword!** Allows you to call this method directly from `main()` without creating an object first. |
| `int` | The **Return Type** (what type of data this function sends back). Use `void` if it returns nothing. |
| `calculateSum` | The name of your function (you pick this name). |
| `(int num1, int num2)` | The input parameters (values sent into the function). |

### C) Clean Modular Example (Keeping `main` Simple)

Notice how in this example, `main()` only handles user input and output, while all calculation and formatting logic is handed off to separate helper functions:

Java

```java
import java.util.Scanner;

public class ModularMethods{

    // Helper Function 1: Check if a number is even
    public static boolean isEven(int number){
        return number % 2 == 0;
    }

    // Helper Function 2: Format and clean a user's name
    public static String formatName(String name){
        return name.trim().toUpperCase();
    }

    // Helper Function 3: Perform addition
    public static int addNumbers(int a, int b){
        return a + b;
    }

    // Main Method (Execution starts here)
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        // 1. Take inputs
        System.out.print("Enter your name: ");
        String rawName = sc.nextLine();

        System.out.print("Enter two numbers separated by space: ");
        int x = sc.nextInt();
        int y = sc.nextInt();

        // 2. Pass inputs to helper functions
        String cleanName = formatName(rawName);
        int sum = addNumbers(x, y);
        boolean evenCheck = isEven(sum);

        // 3. Display results
        System.out.println("\n--- Results ---");
        System.out.println("Hello, " + cleanName + "!");
        System.out.println("Sum of numbers: " + sum);
        System.out.println("Is the sum even? " + evenCheck);

        sc.close();
    }
}
```

### D) Full Combined Master Example

This program brings everything together:

- Takes User Input (`Scanner`)
- Uses String utilities (`replace`, `StringBuilder`, `StringTokenizer`)
- Keeps `main()` clean by delegating tasks to static helper functions

Java

```java
import java.util.Scanner;
import java.util.StringTokenizer;

public class TextProcessorApp{

    // Helper Method 1: Count total words in a sentence
    public static int countWords(String sentence){
        StringTokenizer tokenizer = new StringTokenizer(sentence);
        return tokenizer.countTokens();
    }

    // Helper Method 2: Reverse text using StringBuilder
    public static String reverseText(String text){
        return new StringBuilder(text).reverse().toString();
    }

    // Helper Method 3: Replace all spaces with hyphens
    public static String convertToSlug(String text){
        return text.trim().toLowerCase().replace(" ", "-");
    }

    // Main Function
    public static void main(String[] args){
        Scanner input = new Scanner(System.in);

        System.out.print("Enter a sentence: ");
        String userSentence = input.nextLine();

        // Calling helper methods
        int wordCount = countWords(userSentence);
        String reversed = reverseText(userSentence);
        String slug = convertToSlug(userSentence);

        // Output results
        System.out.println("\n--- Processing Output ---");
        System.out.println("Original Sentence : " + userSentence);
        System.out.println("Total Words       : " + wordCount);
        System.out.println("Reversed Sentence : " + reversed);
        System.out.println("URL Format (Slug) : " + slug);

        input.close();
    }
}
```

### Sample Output:

Plaintext

```
Enter a sentence: Java Programming is Fun

--- Processing Output ---
Original Sentence : Java Programming is Fun
Total Words       : 4
Reversed Sentence : nuF si gnimmargorP avaJ
URL Format (Slug) : java-programming-is-fun
```

## 🧠 Mental Model

`Scanner` is like a **team manager taking player registrations** at a tournament desk:

- `Scanner sc = new Scanner(System.in);` = the manager opens a fresh registration sheet, ready to listen to whoever walks up (the keyboard).
- `nextInt()` = the manager reads *only the number* someone says, e.g. jersey number, and stops right there — leaving the "Enter" they pressed sitting on the desk.
- `nextLine()` right after `nextInt()` = the manager glances down and sees that leftover Enter still sitting there, and mistakes it for "the next player said nothing." That's the trap — you need one throwaway `nextLine()` to clear the desk first.

**Strings being immutable** is like a **printed scorecard from a stadium shop** — you can't edit the ink directly, you can only print a *whole new scorecard* (`replace()`, `substring()` etc. all return new Strings). `StringBuilder` is the manager's **whiteboard** instead — you *can* erase and rewrite on it directly (`append`, `reverse`) without printing a new one each time.

**`.equals()` vs `==`** is like checking "do these two scorecards have the same score written on them" (`.equals()`) versus "are these literally the same physical piece of paper" (`==`) — two different printouts can show identical scores but still be different papers.

## 📌 Key Terms to Remember

- **Buffer** — where input sits before being read (source of the `nextInt`/`nextLine` trap)
- **Immutable** — a `String` cannot be changed after creation; operations return new Strings
- **`StringBuilder`** — mutable text tool for efficient append/reverse/modify
- **`StringTokenizer`** — splits text into tokens based on a delimiter
- **Method** — Java's term for a function, usually `static` when called directly from `main`
