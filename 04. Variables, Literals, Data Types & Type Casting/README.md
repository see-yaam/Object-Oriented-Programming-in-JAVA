# ***04. Variables, Literals, Data Types & Type Casting***

## Table of Contents

1. [Variables & Memory](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/blob/main/04.%20Variables%2C%20Literals%2C%20Data%20Types%20%26%20Type%20Casting/README.md#1-variables--memory)
2. [Literals](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/blob/main/04.%20Variables%2C%20Literals%2C%20Data%20Types%20%26%20Type%20Casting/README.md#2-literals)
3. [Type Conversion & Type Casting](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/blob/main/04.%20Variables%2C%20Literals%2C%20Data%20Types%20%26%20Type%20Casting/README.md#3-type-conversion--type-casting)
4. [Automatic Type Promotion in Expressions](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/blob/main/04.%20Variables%2C%20Literals%2C%20Data%20Types%20%26%20Type%20Casting/README.md#4-automatic-type-promotion-in-expressions)
5. [Comprehensive Cheat Sheet & Reference Table](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/blob/main/04.%20Variables%2C%20Literals%2C%20Data%20Types%20%26%20Type%20Casting/README.md#5-comprehensive-cheat-sheet--reference-table)
6. [🧠 Mental Model](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/blob/main/04.%20Variables%2C%20Literals%2C%20Data%20Types%20%26%20Type%20Casting/README.md#-mental-model)
7. [📌 Key Terms to Remember](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/blob/main/04.%20Variables%2C%20Literals%2C%20Data%20Types%20%26%20Type%20Casting/README.md#-key-terms-to-remember)

---

## 1. Variables & Memory

A **variable** is a named location in the computer's memory that holds a data value during execution. Think of a variable as a labeled storage box: the label is the variable name, the box size is defined by the data type, and the item inside is the value.

### Syntax & Declaration

Java

```
dataType variableName = value;
```

#### Example & Code:

Java

```java
public class VariableBasics{
    public static void main(String[] args){
        // Declaration and Initialization
        int age = 22;               // 32-bit integer box holding 22
        double gpa = 3.85;          // 64-bit decimal box holding 3.85
        char grade = 'A';           // 16-bit Unicode box holding 'A'
        boolean isEnrolled = true;  // Logical flag box holding true

        // Printing values
        System.out.println("Age: " + age);
        System.out.println("GPA: " + gpa);
        System.out.println("Grade: " + grade);
        System.out.println("Enrolled: " + isEnrolled);
    }
}
```

#### Output:

Plaintext

```
Age: 22
GPA: 3.85
Grade: A
Enrolled: true
```

### Variable Naming Rules & Conventions

Java strictly enforces variable naming rules. Violating rules causes **compiler errors**, while ignoring conventions leads to **unreadable code**.

#### Rules vs. Best Practices:

| **Category** | **Valid Example** | **Invalid Example** | **Reason** |
| --- | --- | --- | --- |
| **Starts with Digit** | `int student1;` | `int 1student;` | Identifiers cannot begin with numbers. |
| **Reserved Keywords** | `int myClass;` | `int class;` | `class` is a reserved Java keyword. |
| **Special Characters** | `int $total_score;` | `int total-score;` | Only `_` and `$` special characters are allowed. |
| **Space inside Name** | `int totalScore;` | `int total score;` | Spaces are strictly forbidden in variable names. |
| **Case Sensitivity** | `int age` vs `int Age` | N/A | `age` and `Age` refer to two different memory boxes. |

#### Code Example:

Java

```java
public class NamingRules{
    public static void main(String[] args){
        // Valid Identifiers
        int $money = 500;
        int _score = 99;
        int totalStudentCount = 45; // camelCase convention

        System.out.println("Money: " + $money);
        System.out.println("Score: " + _score);
        System.out.println("Count: " + totalStudentCount);

        // INVALID IDENTIFIERS (Will cause compiler errors if uncommented):
        // int 1stPlace = 1;      // Error: Starts with number
        // int user-name = 5;     // Error: Hyphen not allowed
        // int class = 10;        // Error: Keyword used
    }
}
```

#### Output:

Plaintext

```
Money: 500
Score: 99
Count: 45
```

### Memory Allocation: Primitive Storage (Stack Memory)

All primitive variables (`int`, `double`, `char`, `boolean`, etc.) store their raw value directly inside **Stack Memory**.

Plaintext

```
       +-----------------------+
       |     STACK MEMORY      |
       +-----------------------+
       | age        | 22       |  <-- Direct value stored
       | gpa        | 3.85     |  <-- Direct value stored
       | isEnrolled | true     |  <-- Direct value stored
       +-----------------------+
```

When a primitive variable is assigned to another, Java creates a **complete copy** of the value in memory. Modifying one will never affect the other.

#### Code Example:

Java

```java
public class PrimitiveMemoryCopy{
    public static void main(String[] args){
        int originalValue = 50;
        int copiedValue = originalValue; // Value 50 is duplicated into copiedValue memory box

        originalValue = 100; // Changing original does not change copy

        System.out.println("Original Value: " + originalValue);
        System.out.println("Copied Value: " + copiedValue);
    }
}
```

#### Output:

Plaintext

```
Original Value: 100
Copied Value: 50
```

## 2. Literals

A **literal** is a fixed value written directly into the source code without requiring computation.

Java

```
int count = 100; // '100' is an integer literal
```

### A. Integer Literals (Base Representations & Suffixes)

Java supports four numeral systems for integer literals, as well as readability enhancements like underscores (`_`).

1. **Decimal (Base 10):** Standard digits (`0-9`).
2. **Binary (Base 2):** Prefixed with `0b` or `0B` (uses `0` and `1`).
3. **Octal (Base 8):** Prefixed with `0` (uses digits `0-7`).
4. **Hexadecimal (Base 16):** Prefixed with `0x` or `0X` (uses digits `0-9` and letters `A-F`).

| System | Prefix | Example |
| --- | --- | --- |
| Decimal | none | `100` |
| Binary | `0b`/`0B` | `0b1100100` |
| Octal | `0` | `0144` |
| Hex | `0x`/`0X` | `0x64` |

> **The `L` Suffix:** By default, every integer literal is treated as a 32-bit `int`. If a value exceeds the maximum `int` value ($2,147,483,647$), you must append `L` or `l` to declare it as a 64-bit `long`.
> 

#### Code Example:

Java

```java
public class IntegerLiterals{
    public static void main(String[] args){
        int decimal = 100;
        int binary = 0b1100100;       // 100 in binary
        int octal = 0144;             // 100 in octal
        int hex = 0x64;               // 100 in hexadecimal

        // Underscores for readability (Ignored by Java compiler)
        long phone = 1_800_555_0199L; // Requires 'L' suffix for long literal
        int creditCardCode = 4532_1234;

        System.out.println("Decimal Value: " + decimal);
        System.out.println("Binary (0b1100100): " + binary);
        System.out.println("Octal (0144): " + octal);
        System.out.println("Hexadecimal (0x64): " + hex);
        System.out.println("Formatted Long: " + phone);
        System.out.println("Formatted Int: " + creditCardCode);
    }
}
```

#### Output:

Plaintext

```
Decimal Value: 100
Binary (0b1100100): 100
Octal (0144): 100
Hexadecimal (0x64): 100
Formatted Long: 18005550199
Formatted Int: 45321234
```

### B. Floating-Point Literals (`float` vs `double`)

- By default, any number containing a decimal point (e.g., `3.14`) is treated as a **64-bit `double`**.
- To assign a literal to a **32-bit `float`**, you must explicitly append an `f` or `F` suffix.
- Scientific notation uses `e` or `E` (e.g., $1.23 \times 10^4 = 1.23\text{e}4$).

#### Code Example:

Java

```java
public class FloatingPointLiterals{
    public static void main(String[] args){
        double defaultDouble = 3.1415926535; // 64-bit double literal
        float explicitFloat = 3.14159f;      // 32-bit float literal (requires 'f')

        // Scientific notation
        double scientific1 = 1.23e4;   // 1.23 * 10^4 = 12300.0
        double scientific2 = 5.67e-3;  // 5.67 * 10^-3 = 0.00567

        System.out.println("Double Value: " + defaultDouble);
        System.out.println("Float Value: " + explicitFloat);
        System.out.println("Scientific 1.23e4: " + scientific1);
        System.out.println("Scientific 5.67e-3: " + scientific2);
    }
}
```

#### Output:

Plaintext

```
Double Value: 3.1415926535
Float Value: 3.14159
Scientific 1.23e4: 12300.0
Scientific 5.67e-3: 0.00567
```

### C. Character & String Literals

- **Character Literals (`char`):** Enclosed in **single quotes** (`'A'`). Can store single characters, escape sequences, or 16-bit Unicode hex values (`\uXXXX`).
- **String Literals (`String`):** Enclosed in **double quotes** (`"Hello"`).

#### Escape Sequences Table:

| **Escape Sequence** | **Name** | **Description** |
| --- | --- | --- |
| `\n` | Newline | Moves cursor to the beginning of the next line. |
| `\t` | Tab | Inserts a horizontal tab space. |
| `\\` | Backslash | Prints a literal backslash character (`\`). |
| `\"` | Double Quote | Prints a literal double quote inside string literals. |
| `\'` | Single Quote | Prints a literal single quote inside character literals. |

#### Code Example:

Java

```
public class CharacterLiterals{
    public static void main(String[] args){
        char letter = 'J';
        char unicodeBengali = '\u0985'; // Unicode representation of 'অ'
        char asciiCode = 66;            // ASCII 66 corresponds to 'B'

        // Escape sequences demonstration
        String escapedText = "Line 1\nLine 2\tIndented\nPath: C:\\Java\\Bin\nHe said: \"Hello!\"";

        System.out.println("Letter: " + letter);
        System.out.println("Unicode Char: " + unicodeBengali);
        System.out.println("ASCII Char: " + asciiCode);
        System.out.println("--- Escaped Text ---");
        System.out.println(escapedText);
    }
}
```

#### Output:

Plaintext

```
Letter: J
Unicode Char: অ
ASCII Char: B
--- Escaped Text ---
Line 1
Line 2	Indented
Path: C:\Java\Bin
He said: "Hello!"
```

### D. Boolean Literals

Boolean literals in Java consist strictly of two keywords: **`true`** and **`false`**.

> **Crucial Difference from C/C++:** In C, integers like `1` or `0` can represent boolean flags. In Java, `boolean` is a distinct type and **cannot** be converted to or from integers.
> 

#### Code Example:

Java

```
public class BooleanLiterals{
    public static void main(String[] args){
        boolean isJavaFun = true;
        boolean isFishFlying = false;

        System.out.println("Is Java Fun? " + isJavaFun);
        System.out.println("Is Fish Flying? " + isFishFlying);

        // INVALID IN JAVA (Uncommenting causes compiler error):
        // boolean invalidBool = 1; // Error: incompatible types: int cannot be converted to boolean
    }
}
```

#### Output:

Plaintext

```
Is Java Fun? true
Is Fish Flying? false
```

## 3. Type Conversion & Type Casting

Type conversion converts a value from one data type to another. It falls into two major categories: **Widening (Implicit)** and **Narrowing (Explicit)**.

Plaintext

```
                     Widening (Automatic / Safe)
  byte ──> short ──> int ──> long ──> float ──> double
           char ──┘
<────────────────────────────────────────────────────────
                     Narrowing (Explicit / Data Loss Risk)
```

### A. Widening (Implicit / Automatic) Casting

Widening casting happens automatically when transferring a value from a smaller data type to a larger target data type size. Because the destination type has more storage capacity, no data loss can occur.

#### Step-by-Step Execution:

1. `byte` (8-bit) expands to `short` or `int` (16/32-bit).
2. `int` (32-bit) expands to `long` (64-bit) or `double` (64-bit floating-point).

#### Code Example:

Java

```
public class WideningCasting{
    public static void main(String[] args){
        byte myByte = 42;
        int myInt = myByte;          // Automatic implicit casting: byte -> int
        long myLong = myInt;          // Automatic implicit casting: int -> long
        float myFloat = myLong;       // Automatic implicit casting: long -> float
        double myDouble = myFloat;    // Automatic implicit casting: float -> double

        System.out.println("Byte Value: " + myByte);
        System.out.println("Int Value: " + myInt);
        System.out.println("Long Value: " + myLong);
        System.out.println("Float Value: " + myFloat);
        System.out.println("Double Value: " + myDouble);
    }
}
```

#### Output:

Plaintext

```
Byte Value: 42
Int Value: 42
Long Value: 42
Float Value: 42.0
Double Value: 42.0
```

### B. Narrowing (Explicit / Manual) Casting

Narrowing casting happens when converting a larger data type into a smaller target type. You must place the target type in parentheses `(targetType)` before the variable.

> **Risks of Narrowing:**
> 
> 1. **Truncation:** Fractional digits of floating-point numbers are discarded.
> 2. **Data Overflow / Wrap-Around:** If the number exceeds the target type's min/max range, binary overflow alters the value completely.

Java

```
targetDataType variable = (targetDataType) originalValue;
```

#### Mathematical Mechanics of Overflow (Why 130 becomes -126 in a `byte`):

- `byte` range: -128 to 127
- 130 in binary (32-bit int): `00000000 00000000 00000000 10000010`
- Casting to 8-bit `byte` keeps only the last 8 bits: `10000010`
- In two's complement, a leading `1` = negative → `10000010` = **126**

#### Code Example:

Java

```java
public class NarrowingCasting{
    public static void main(String[] args){
        // 1. Truncation Example (Double -> Int)
        double exactPrice = 199.99;
        int roundedPrice = (int) exactPrice; // Fractional .99 is chopped off

        // 2. Data Overflow Example (Int -> Byte)
        int largeNumber = 130;
        byte overflowedByte = (byte) largeNumber; // 130 exceeds byte max value (127)

        // 3. Int -> Char Conversion
        int asciiVal = 67;
        char character = (char) asciiVal;

        System.out.println("Original Double: " + exactPrice);
        System.out.println("Casted Int (Truncated): " + roundedPrice);
        System.out.println("Original Int: " + largeNumber);
        System.out.println("Casted Byte (Overflowed): " + overflowedByte);
        System.out.println("Casted Char from 67: " + character);
    }
}
```

#### Output:

Plaintext

```
Original Double: 199.99
Casted Int (Truncated): 199
Original Int: 130
Casted Byte (Overflowed): -126
Casted Char from 67: C
```

## 4. Automatic Type Promotion in Expressions

When performing operations inside arithmetic expressions, Java automatically promotes the data types of operands before calculating the result according to two strict rules:

### Rule 1: The Small Integer Promotion Rule

All `byte`, `short`, and `char` operands are **automatically promoted to `int`** before evaluation.

Java

```java
byte a = 10;
byte b = 20;
// a + b is evaluated as (int)a + (int)b
```

### Rule 2: The Dominant Operand Rule

If an expression contains operands of higher-precision data types, the entire expression is promoted to match the highest-precision type:

- If any operand is `double`, the result is **`double`**.
- Else if any operand is `float`, the result is **`float`**.
- Else if any operand is `long`, the result is **`long`**.

Plaintext

```
Operand Types in Expression               Promoted Result Type
---------------------------               --------------------
byte + short + char                       --> int
int + long                                --> long
long + float                              --> float
float + double                            --> double
```

### Code Examples & Compiler Errors

#### Example 1: Small Integer Promotion Error & Fix

Java

```
public class TypePromotionBasics{
    public static void main(String[] args){
        byte b1 = 40;
        byte b2 = 50;

        // COMPILER ERROR CODE (If uncommented):
        // byte b3 = b1 * b2;
        // Reason: 'b1 * b2' generates an 'int' result (2000). Cannot assign 'int' to 'byte'.

        // CORRECT FIX 1: Assign result to an int
        int resultInt = b1 * b2;

        // CORRECT FIX 2: Explicitly cast result back to byte
        byte resultByte = (byte)(b1 * b2); // 2000 casted to byte causes overflow

        System.out.println("Result stored in int: " + resultInt);
        System.out.println("Result casted back to byte (Overflow): " + resultByte);
    }
}
```

#### Output:

Plaintext

```
Result stored in int: 2000
Result casted back to byte (Overflow): -48
```

#### Example 2: Dominant Operand Promotion (`char`, `int`, `double`)

Java

```
public class ExpressionPromotion{
    public static void main(String[] args){
        char charVal = 'a';     // ASCII value 97
        int intVal = 10;
        float floatVal = 5.5f;
        double doubleVal = 10.5;

        // Expression evaluation breakdown:
        // (charVal * intVal) + (floatVal / intVal) - doubleVal
        //    (97 * 10)       +  (5.5f / 10)       - 10.5
        //     970 (int)      +   0.55f (float)    - 10.5 (double)
        //          970.55f (float)                - 10.5 (double)
        //                   960.05 (double)

        double finalResult = (charVal * intVal) + (floatVal / intVal) - doubleVal;

        System.out.println("Final Expression Result: " + finalResult);
    }
}
```

#### Output:

Plaintext

```
Final Expression Result: 960.05
```

## 5. Comprehensive Cheat Sheet & Reference Table

| **Concept** | **Automatic?** | **Syntax / Example** | **Risk / Side Effect** |
| --- | --- | --- | --- |
| **Variable Declaration** | Manual | `int count = 10;` | Uninitialized variables cause compiler errors. |
| **Primitive Stack Copy** | Automatic | `int b = a;` | Creates independent values; modifying `a` does not affect `b`. |
| **`long` Literal** | Manual | `long num = 3000000000L;` | Missing `L` causes "Integer number too large" compiler error. |
| **`float` Literal** | Manual | `float val = 2.5f;` | Missing `f` causes "Incompatible types: double to float" error. |
| **Widening Cast** | Automatic | `double d = 100;` | 100% safe. No data loss. |
| **Narrowing Cast** | Manual | `int i = (int) 99.9;` | Truncates decimal part (`.9` lost). Risk of binary overflow. |
| **Small Promotion** | Automatic | `byte + byte` $\rightarrow$ `int` | Assigning back to `byte` directly without cast causes error. |
| **Dominant Promotion** | Automatic | `int + double` $\rightarrow$ `double` | Expression elevates to the highest precision operand type. |

## 🧠 Mental Model

Think of variables as **scorecards in a cricket stats sheet**:

- Each column (variable) has a fixed **box size** — a "runs" column can't suddenly hold a player's whole biography.
- **Widening cast** = moving a player's stat from a small local scoreboard (byte) to the full international stats database (double) — always safe, nothing gets lost.
- **Narrowing cast** = trying to cram the full international database stat back onto a tiny local scoreboard — if the number is too big, digits get chopped off and the scoreboard shows something completely wrong (**overflow**), just like a scoreboard rolling over from 99 to 00.
- **Type promotion** in expressions is like a match rule: "if any team in this comparison is playing at the international (double) level, the whole comparison is judged at international level" — you don't mix formats mid-calculation.

## 📌 Key Terms to Remember

- **Widening casting** — automatic, safe, small→large type
- **Narrowing casting** — manual, risky, large→small type
- **Truncation** — decimal part chopped off during narrowing
- **Overflow** — value wraps around when it exceeds the target type's range
- **Literal** — a fixed value written directly in code
- **Type promotion** — automatic upgrade of operand types inside an expression
