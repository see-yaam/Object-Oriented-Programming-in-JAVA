# ***05. Operators in Java***

## Table of Contents

1. [Arithmetic Operators](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/05.%20Operators%20in%20Java#1-arithmetic-operators)
2. [Unary & Increment / Decrement Operators](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/05.%20Operators%20in%20Java#2-unary--increment--decrement-operators)
3. [Relational & Logical Operators (Short-Circuit Evaluation)](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/05.%20Operators%20in%20Java#3-relational--logical-operators-short-circuit-evaluation)
4. [Assignment & Ternary Operators](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/05.%20Operators%20in%20Java#4-assignment--ternary-operators)
5. [Bitwise & Shift Operators](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/05.%20Operators%20in%20Java#5-bitwise--shift-operators)
6. [Operator Precedence & Associativity Table(High→Low)](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/05.%20Operators%20in%20Java#6-operator-precedence--associativity-tablehighlow)
7. [Comprehensive Cheat Sheet & Summary](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/05.%20Operators%20in%20Java#7-comprehensive-cheat-sheet--summary)
8. [🧠 Mental Model](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/05.%20Operators%20in%20Java#-mental-model)
9. [📌 Key Terms to Remember](https://github.com/see-yaam/Object-Oriented-Programming-in-JAVA/tree/main/05.%20Operators%20in%20Java#-key-terms-to-remember)

---

An **operator** is a symbol that performs specific operations on one, two, or three operands and produces a result.

### 1. Arithmetic Operators

Used to perform basic mathematical operations.

| **Operator** | **Name** | **Example** | **Description** |
| --- | --- | --- | --- |
| `+` | Addition | `a + b` | Adds two values (or concatenates Strings). |
| `-` | Subtraction | `a - b` | Subtracts second value from first. |
| `*` | Multiplication | `a * b` | Multiplies two values. |
| `/` | Division | `a / b` | Divides numerator by denominator. |
| `%` | Modulus | `a % b` | Returns the remainder of division. |

> **Integer Division Pitfall:** Dividing two integers in Java produces an **integer result** (truncates remainder). To get decimal precision, at least one operand must be a floating-point type (`float` or `double`).
> 

#### Code Example:

Java

```java
public class ArithmeticOperators{
    public static void main(String[] args){
        int x = 15;
        int y = 4;

        System.out.println("Addition (x + y): " + (x + y));
        System.out.println("Subtraction (x - y): " + (x - y));
        System.out.println("Multiplication (x * y): " + (x * y));
        System.out.println("Integer Division (x / y): " + (x / y));     // Truncates decimal
        System.out.println("Double Division ((double)x / y): " + ((double) x / y)); // Preserves decimal
        System.out.println("Modulus Remainder (x % y): " + (x % y));
    }
}
```

#### Output:

Plaintext

```
Addition (x + y): 19
Subtraction (x - y): 11
Multiplication (x * y): 60
Integer Division (x / y): 3
Double Division ((double)x / y): 3.75
Modulus Remainder (x % y): 3
```

### 2. Unary & Increment / Decrement Operators

Operate on a single operand.

| **Operator** | **Description** |
| --- | --- |
| `+` | Unary plus (indicates positive value). |
| `-` | Unary minus (negates an expression). |
| `++var` | **Prefix Increment:** Increments value *before* evaluating expression. |
| `var++` | **Postfix Increment:** Evaluates expression *first*, then increments value. |
| `--var` | **Prefix Decrement:** Decrements value *before* evaluating expression. |
| `var--` | **Postfix Decrement:** Evaluates expression *first*, then decrements value. |
| `!` | Logical NOT (inverts boolean value). |

#### Code Example:

Java

```java
public class UnaryOperators{
    public static void main(String[] args){
        int a = 5;
        int b = 5;

        // Prefix vs Postfix Increment
        int prefixResult = ++a;  // 'a' becomes 6 first, then assigned to prefixResult
        int postfixResult = b++; // 'b' (5) is assigned to postfixResult first, then 'b' becomes 6

        System.out.println("Prefix Result (++a): " + prefixResult + " | Final a: " + a);
        System.out.println("Postfix Result (b++): " + postfixResult + " | Final b: " + b);

        boolean flag = true;
        System.out.println("Negated Boolean (!flag): " + !flag);
    }
}
```

#### Output:

Plaintext

```
Prefix Result (++a): 6 | Final a: 6
Postfix Result (b++): 5 | Final b: 6
Negated Boolean (!flag): false
```

### 3. Relational & Logical Operators (Short-Circuit Evaluation)

- **Relational Operators:** Compare two values and return a `boolean` (`==`, `!=`, `>`, `<`, `>=`, `<=`).
- **Logical Operators:** Combine boolean expressions (`&&`, `||`, `!`).

> **Short-Circuit Evaluation:**
> 
> - **`&&` (Logical AND):** If the left operand is `false`, Java **skips** evaluating the right operand completely (because the result is guaranteed to be `false`).
> - **`||` (Logical OR):** If the left operand is `true`, Java **skips** evaluating the right operand completely (because the result is guaranteed to be `true`).

#### Code Example:

Java

```java
public class LogicalOperators{
    public static void main(String[] args){
        int age = 20;
        boolean hasLicense = true;

        // Relational + Logical evaluation
        boolean canDrive = (age >= 18) && hasLicense;
        System.out.println("Can drive: " + canDrive);

        // Demonstrating Short-Circuiting
        int count = 10;
        // Since (count > 20) is FALSE, (++count < 100) is NEVER executed!
        if (count > 20 && ++count < 100) {
            System.out.println("Inside IF statement");
        }

        System.out.println("Count value after short-circuit test: " + count);
    }
}
```

#### Output:

Plaintext

```
Can drive: true
Count value after short-circuit test: 10
```

### 4. Assignment & Ternary Operators

#### Assignment Operators

Combines arithmetic operations with variable assignment (`+=`, `-=`, `*=`, `/=`, `%=`).

> **Built-in Casting Benefit:** Compound assignment operators implicitly cast the result to the variable's original type!
> 

Java

```java
byte b = 10;
// b = b + 5;  // COMPILER ERROR: int cannot be assigned to byte
b += 5;        // VALID: Equivalent to b = (byte)(b + 5)
```

#### Ternary Operator

Shorthand for `if-else` statement taking three operands.

Java

```java
variable = (condition) ? valueIfTrue : valueIfFalse;
```

#### Code Example:

Java

```java
public class AssignmentAndTernary{
    public static void main(String[] args){
        // Compound Assignment
        int balance = 100;
        balance += 50; // balance = balance + 50
        balance *= 2;  // balance = balance * 2
        System.out.println("Updated Balance: " + balance);

        // Ternary Operator
        int score = 75;
        String status = (score >= 40) ? "PASS" : "FAIL";
        System.out.println("Exam Result: " + status);

        // Nested Ternary Example (Find Maximum of 2 numbers)
        int num1 = 45, num2 = 82;
        int max = (num1 > num2) ? num1 : num2;
        System.out.println("Max Number: " + max);
    }
}
```

#### Output:

Plaintext

```
Updated Balance: 300
Exam Result: PASS
Max Number: 82
```

### 5. Bitwise & Shift Operators

Bitwise operators manipulate individual bits of integer data types (`byte`, `short`, `int`, `long`).

| **Operator** | **Name** | **Description** | **Example (a=5, b=3)** |
| --- | --- | --- | --- |
| `&` | Bitwise AND | Sets bit to 1 if both bits are 1. | `5 & 3` (0101 & 0011 = 0001 = 1) |
| `|` | Bitwise OR | Sets bit to 1 if either bit is 1. | `5 | 3` (0101 | 0011 = 0111 = 7) |
| `^` | Bitwise XOR | Sets bit to 1 if bits are different. | `5 ^ 3` (0101 ^ 0011 = 0110 = 6) |
| `~` | Bitwise NOT | Inverts all bits (Two's complement). | `~5` (~00000101 = -6) |
| `<<` | Left Shift | Shifts bits left, fills right with 0 (x * 2^n). | `5 << 1` (5 * 2 = 10) |
| `>>` | Signed Right Shift | Shifts bits right, preserves sign bit (x / 2^n). | `20 >> 2` (20 / 4 = 5) |
| `>>>` | Unsigned Right Shift | Shifts bits right, fills left with 0s regardless of sign. | `-20 >>> 2` (= 1073741819) |

#### Code Example:

Java

```java
public class BitwiseOperators{
    public static void main(String[] args){
        int a = 5;  // Binary: 0000 0101
        int b = 3;  // Binary: 0000 0011

        System.out.println("Bitwise AND (a & b): " + (a & b));
        System.out.println("Bitwise OR  (a | b): " + (a | b));
        System.out.println("Bitwise XOR (a ^ b): " + (a ^ b));
        System.out.println("Bitwise NOT (~a):    " + (~a));

        // Shift Operators
        int val = 8; // Binary: 0000 1000
        System.out.println("Left Shift (8 << 2):  " + (val << 2)); // 8 * 2^2 = 32
        System.out.println("Right Shift (8 >> 2): " + (val >> 2)); // 8 / 2^2 = 2
    }
}
```

#### Output:

Plaintext

```
Bitwise AND (a & b): 1
Bitwise OR  (a | b): 7
Bitwise XOR (a ^ b): 6
Bitwise NOT (~a):    -6
Left Shift (8 << 2):  32
Right Shift (8 >> 2): 2
```

### 6. Operator Precedence & Associativity Table(High→Low)

Higher operators in the table are evaluated **first**.

| **Category** | **Operator** | **Associativity** |
| --- | --- | --- |
| **Postfix** | `expr++` `expr--` | Left to Right |
| **Unary** | `++expr` `--expr` `+` `-` `!` `~` | Right to Left |
| **Multiplicative** | `*` `/` `%` | Left to Right |
| **Additive** | `+` `-` | Left to Right |
| **Shift** | `<<` `>>` `>>>` | Left to Right |
| **Relational** | `<` `>` `<=` `>=` `instanceof` | Left to Right |
| **Equality** | `==` `!=` | Left to Right |
| **Bitwise AND** | `&` | Left to Right |
| **Bitwise XOR** | `^` | Left to Right |
| **Bitwise OR** | ` | ` |
| **Logical AND** | `&&` | Left to Right |
| **Logical OR** | ` |  |
| **Ternary** | `? :` | Right to Left |
| **Assignment** | `=` `+=` `-=` `*=` `/=` `%=` `&=` `^=` ` | = ``<<= ``>>= ``>>>=` |

## 7. Comprehensive Cheat Sheet & Summary

| **Concept** | **Syntax Example** | **Key Takeaway / Pitfall** |
| --- | --- | --- |
| **`long` Literal** | `long n = 10000000000L;` | Requires `L` suffix if value exceeds 32-bit `int` max. |
| **`float` Literal** | `float f = 2.5f;` | Requires `f` suffix; default floating-point literal is `double`. |
| **Implicit Cast** | `double d = 10;` | Automatic widening; 100% safe without data loss. |
| **Explicit Cast** | `int i = (int) 9.99;` | Manual narrowing; truncates decimal portion (`.99` lost). |
| **Type Promotion** | `byte + byte` $\rightarrow$ `int` | Expressions promote small integer types to `int` automatically. |
| **Integer Division** | `5 / 2` $\rightarrow$ `2` | Integer division drops decimals. Use `5.0 / 2` for `2.5`. |
| **Post vs Pre Inc** | `i++` vs `++i` | `++i` increments first; `i++` evaluates expression first. |
| **Short-Circuiting** | `a && b`, `a || b` | Skips second operand evaluation if final boolean result is determined by first. |
| **Ternary Operator** | `x > y ? x : y` | Compact conditional evaluation returning a value. |

## 🧠 Mental Model

Think of operators as **umpire signals during a match**:

- **Arithmetic operators** are the basic scoring math — runs added, overs divided. Integer division dropping the decimal is like an umpire announcing "3 overs" instead of "3.75 overs" — technically true but missing the fractional detail.
- **Short-circuit `&&`/`||`** are like an umpire who stops checking replays the moment the result is already certain — if the batsman is clearly not out on the first camera angle, he doesn't bother checking three more angles.
- **Bitwise operators** are like comparing two teams' selection sheets bit-by-bit — "did both teams pick this player? (AND)" or "did either team pick this player? (OR)".
- **Precedence** is match rules: multiplication (run-rate math) always resolves before comparison (who's ahead), just like overs bowled always get counted before the match result is declared.

## 📌 Key Terms to Remember

- **Short-circuit evaluation** — skipping the second operand when the result is already determined
- **Compound assignment** — `+=`, `=` etc., which auto-cast back to the original type
- **Ternary operator** — `condition ? valueIfTrue : valueIfFalse`
- **Bitwise operators** — operate on individual bits (`&`, `|`, `^`, `~`, `<<`, `>>`, `>>>`)
- **Operator precedence** — the order operators are evaluated in a mixed expression
