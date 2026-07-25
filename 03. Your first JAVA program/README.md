# ***03. Your first JAVA program: Hello World***

The standard Java "Hello World" program serves as the entry point for understanding Java syntax, structure, and execution semantics.

## 1. Complete Source Code

Java

```java
public class Main{
    public static void main(String[] args){
        System.out.println("Hello, World!");
    }
}
```

## 2. Word-by-Word Technical Anatomy

### Line 1: Class Definition (`public class Main`)

Java

```java
public class Main
```

- **`public`** *(Access Modifier)*: Declares the visibility of the class. Marking a class `public` means it can be accessed from any other package in the Java runtime environment.
- **`class`** *(Keyword)*: The core building block of Java. Every executable statement in Java must reside inside a class definition.
- **`Main`** *(Identifier)*: The name of the class.
    
    > **Note:** In Java, if a class is declared `public`, the filename **must match** the class name exactly (including case). Therefore, this file must be saved as `Main.java`.
    > 

### Line 2: The Main Method (`public static void main(String[] args)`)

Java

```java
public static void main(String[] args)
```

This specific method signature is the **standard execution entry point** recognized by the Java Virtual Machine (JVM).

- **`public`** *(Access Modifier)*: Makes the method accessible to the JVM from outside the class context during execution.
- **`static`** *(Keyword)*: Allows the JVM to invoke the `main` method **without instantiating** an object of the `Main` class. It exists in class memory right when the class is loaded.
- **`void`** *(Return Type)*: Specifies that this method does not return any value back to the caller (the JVM).
- **`main`** *(Method Identifier)*: The exact method name the JVM looks for to start program execution.
- **`String[]`** *(Data Type)*: Indicates an array of `String` objects.
- **`args`** *(Variable Name)*: Short for "arguments". It holds command-line inputs passed to the application at launch.

### Line 3: Output Statement (`System.out.println("Hello, World!");`)

Java

```java
System.out.println("Hello, World!");
```

- **`System`** *(Built-in Class)*: A `final` class provided by the `java.lang` package containing utility methods and system resources.
- **`out`** *(Static Field)*: An instance of `java.io.PrintStream` held as a static member in the `System` class. It represents the **Standard Output Stream** (the terminal/console).
- **`println()`** *(Method)*: Short for "print line". It outputs the provided parameter to the standard output and appends a new line (`\n`) character at the end. We can skip `ln`  if we don;t want any new line.
- **`"Hello, World!"`** *(String Literal)*: The exact text data passed as an argument to the `println()` method.
- **`;`** *(Semicolon)*: The statement terminator in Java syntax. It informs the compiler that the instruction ends here.

## 3. Deep Dive: What Does the Dot (`.`) Operator Mean?

In Java, the dot (`.`) operator is the **Member Access Operator**. It is used to access fields, methods, or nested structures within a class, package, or object reference.

```
System  .  out  .  println("Hello, World!");
 │          │        │
 │          │        └─> 3. Call the method inside PrintStream
 │          └─> 2. Access the static stream field inside System
 └─> 1. Target the System class
```

1. **`System.out`**: Accesses the static field `out` defined inside the `System` class.
2. **`out.println()`**: Accesses and calls the `println()` method attached to that `out` stream object.
