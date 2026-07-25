# ***06. Control Flow Statements***

By default, Java executes statements sequentially from top to bottom. However, real-world applications require making decisions based on conditions or executing a block of code repeatedly.

**Control Flow Statements** break the sequential execution flow and allow you to direct how your program runs.

Java categorizes Control Flow Statements into three main groups:

1. **Decision-Making (Conditional) Statements:** `if`, `if-else`, `if-else-if`, `switch`
2. **Looping (Iterative) Statements:** `while`, `do-while`, `for`, `for-each`
3. **Branching / Jump Statements:** `break`, `continue`, `return`, `Labeled Statements`

## 1. Decision-Making Statements

Decision-making statements execute specific blocks of code based on whether a boolean condition evaluates to `true` or `false`.

### A) Simple `if` Statement

Executes a block of code **only** if the specified condition is `true`.

Java

```java
int age = 20;

if (age >= 18) {
    System.out.println("You are eligible to vote!");
}
```

### B) `if-else` Statement

Executes the `if` block if the condition is `true`, and the `else` block if the condition is `false`.

Java

```java
int number = 7;

if (number % 2 == 0) {
    System.out.println("Even Number");
} else {
    System.out.println("Odd Number");
}
```

### C) `if-else-if` Ladder

Evaluates multiple conditions sequentially. The first condition that evaluates to `true` executes its corresponding block, skipping the rest.

Java

```java
int marks = 75;

if (marks >= 80) {
    System.out.println("Grade: A+");
} else if (marks >= 70) {
    System.out.println("Grade: A");
} else if (marks >= 60) {
    System.out.println("Grade: A-");
} else {
    System.out.println("Grade: Fail");
}
```

### D) Nested `if-else`

An `if` or `else` block containing another `if-else` statement inside it.

Java

```java
int age = 25;
boolean hasLicense = true;

if (age >= 18) {
    if (hasLicense) {
        System.out.println("You can drive!");
    } else {
        System.out.println("You need a driver's license.");
    }
} else {
    System.out.println("You are underage to drive.");
}
```

### ⚠️ Pitfall: The Dangling `else` Problem

In Java, an `else` block always pairs with the **closest unclosed `if` statement**, regardless of code indentation.

Java

```java
// Misleading indentation example:
if (a > 10)
    if (b > 20)
        System.out.println("Both True");
else
    System.out.println("Which IF does this belong to?");
    // This 'else' actually attaches to (b > 20), NOT (a > 10)!
```

> **Best Practice:** Always enclose `if` and `else` blocks in curly braces `{}` to avoid ambiguity.
> 

### E) `switch` Statement (Traditional vs. Modern)

The `switch` statement selects one of many code blocks to execute based on a single value. It is cleaner and more performant than a long `if-else-if` chain.

#### 1. Traditional `switch`

- **Supported Data Types:** `byte`, `short`, `char`, `int`, `String`, and `Enum` (does **not** support `long`, `float`, `double`, or `boolean`).
- **Fall-Through Behavior:** Without a `break` statement at the end of a case, execution "falls through" into subsequent cases automatically.

Java

```java
int day = 2;

switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break; // Prevents fall-through to Wednesday
    case 3:
        System.out.println("Wednesday");
        break;
    default:
        System.out.println("Invalid Day");
}
```

#### 2. Enhanced `switch` Expression (Java 14+)

Modern Java introduces arrow syntax (`->`) that eliminates fall-through bugs and allows returning values directly without requiring `break` statements.

Java

```java
int day = 2;

// Arrow syntax with direct value return
String dayName = switch (day) {
    case 1 -> "Monday";
    case 2 -> "Tuesday";
    case 3 -> "Wednesday";
    case 4, 5, 6, 7 -> "Weekend/Other Days"; // Grouping multiple labels
    default -> "Invalid Day";
};

System.out.println("Day is: " + dayName);
```

## 2. Looping (Iterative) Statements

Loops execute a block of code repeatedly as long as a specified condition remains `true`.

### A) `while` Loop (Pre-Test Loop)

Evaluates the condition **before** executing the loop body. If the initial condition is `false`, the loop body never runs.

Java

```java
int count = 1;

while (count <= 3) {
    System.out.println("Count: " + count);
    count++;
}
```

### B) `do-while` Loop (Post-Test Loop)

Executes the loop body **first**, then evaluates the condition. Guarantees that the loop body executes **at least once**, even if the condition is initially `false`.

Java

```java
int count = 5;

do {
    System.out.println("Executes at least once. Count: " + count);
    count++;
} while (count <= 3); // Condition is false, but body executed once
```

### C) Standard `for` Loop

Ideal when the exact number of iterations is known in advance. Consists of three parts: `for (Initialization; Condition; Update)`.

Java

```java
for (int i = 1; i <= 3; i++) {
    System.out.println("Iteration: " + i);
}
```

#### 💡 Advanced `for` Loop Features:

1. **Multiple Control Variables (Comma Operator):**

Java

```java
for (int i = 0, j = 10; i < j; i++, j--) {
    System.out.println("i: " + i + ", j: " + j);
}
```

1. **Infinite `for` Loop:**

Java

```java
for (;;) {
    // Infinite loop equivalent to while(true)
}
```

### D) Enhanced `for` Loop (`for-each`)

Designed specifically for iterating over elements in Arrays or Collections cleanly, without managing an explicit index counter.

Java

```java
int[] numbers = {10, 20, 30, 40};

for (int num : numbers) {
    System.out.println("Number: " + num);
}
```

### ⚠️ Pitfall: Floating-Point Loop Counters

Avoid using `float` or `double` variables as loop control counters due to precision limitations in binary floating-point representation.

Java

```java
// Dangerous Infinite Loop Risk!
for (double d = 0.0; d != 1.0; d += 0.1) {
    System.out.println(d); // Precision errors may prevent d from ever being exactly 1.0
}
```

## 3. Branching / Jump Statements

Jump statements alter execution by transferring control to another part of the program immediately.

### A) `break` Statement

Terminates the innermost enclosing loop or `switch` block immediately.

Java

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break; // Stops the loop completely when i reaches 5
    }
    System.out.print(i + " "); // Output: 1 2 3 4
}
```

### B) `continue` Statement

Skips the remaining statements in the current loop iteration and moves directly to the next iteration.

Java

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue; // Skips printing 3 and proceeds to i = 4
    }
    System.out.print(i + " "); // Output: 1 2 4 5
}
```

### C) Labeled `break` & `continue` Statements

Standard `break` and `continue` statements apply only to the innermost loop. Labels allow breaking out of or skipping iterations in an **outer loop** from inside a nested loop.

#### Labeled `break` Example:

Java

```java
outerLoop: // Label identifier
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        if (i == 2 && j == 2) {
            break outerLoop; // Terminates the outer loop directly
        }
        System.out.println("i=" + i + ", j=" + j);
    }
}
```

#### Labeled `continue` Example:

Java

```java
outerLoop:
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        if (j == 2) {
            continue outerLoop; // Jumps directly to next iteration of outerLoop
        }
        System.out.println("i=" + i + ", j=" + j);
    }
}
```

### D) `return` Statement

Exits from the current method entirely and passes control back to the caller, optionally returning a value.

Java

```java
public class ReturnExample{
    public static void main(String[] args){
        checkAge(15);
        System.out.println("This line in main executes.");
    }

    static void checkAge(int age){
        if (age < 18) {
            System.out.println("Access Denied!");
            return; // Exits method immediately
        }
        System.out.println("Access Granted!");
    }
}
```

## 4. Summary & Comparison Table

| **Statement** | **Purpose** | **Key Characteristics / Pitfalls** |
| --- | --- | --- |
| `if-else` | Range or complex logical checks | Beware of Dangling Else without curly braces `{}`. |
| `switch` | Value matching against discrete inputs | Traditional syntax requires `break`; Enhanced syntax uses `->`. |
| `while` | Loop with condition evaluated first | Pre-test loop; executes 0 or more times. |
| `do-while` | Loop executed before condition evaluation | Post-test loop; guaranteed to execute at least 1 time. |
| `for` | Known iteration count loop | Keeps Initialization, Condition, and Update together. |
| `for-each` | Read-only iteration over collections | Clean syntax; cannot modify array structure or access index. |
| `break` | Exits loop or switch statement | Use Labeled `break` for nested loop exit. |
| `continue` | Skips current iteration | Use Labeled `continue` for outer loop skip. |
| `return` | Exits from current method | Can return data back to caller. |

## 5. Comprehensive Master Example

Java

```java
public class ControlFlowMaster{
    public static void main(String[] args){
        int[] scores = {45, 82, 90, 33, 100, -1};

        System.out.println("--- Processing Student Scores ---");

        outerProcessing:
        for (int score : scores) {
            // 1. Jump Statement Check
            if (score < 0) {
                System.out.println("Negative score found (" + score + "). Terminating process!");
                break outerProcessing; // Labeled Break
            }

            if (score < 40) {
                System.out.println("Score: " + score + " -> Failed! Skipping detailed report.");
                continue; // Skip remaining loop processing
            }

            // 2. Decision Making (if-else)
            String status;
            if (score >= 90) {
                status = "Excellent";
            } else {
                status = "Passed";
            }

            // 3. Enhanced Switch Expression (Java 14+)
            int category = score / 10;
            String gradeLetter = switch (category) {
                case 10, 9 -> "A+";
                case 8     -> "A";
                case 7     -> "B";
                default    -> "C";
            };

            System.out.println("Score: " + score + " | Status: " + status + " | Grade: " + gradeLetter);
        }
    }
}
```

#### Output:

Plaintext

```
--- Processing Student Scores ---
Score: 45 | Status: Passed | Grade: C
Score: 82 | Status: Passed | Grade: A
Score: 90 | Status: Excellent | Grade: A+
Score: 33 -> Failed! Skipping detailed report.
Score: 100 | Status: Excellent | Grade: A+
Negative score found (-1). Terminating process!
```
