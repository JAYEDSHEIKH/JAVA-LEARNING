# Java Complete Guide — Beginner to Advanced

> Java is the language behind Minecraft, Android apps, and countless enterprise systems.
> This guide starts from zero and builds up step by step — no prior experience needed.

---

## Table of Contents

### 🟢 Beginner
1. [What is Java?](#1-what-is-java)
2. [Your First Program](#2-your-first-program)
3. [Variables & Data Types](#3-variables--data-types)
4. [Getting Input from User](#4-getting-input-from-user)
5. [Operators](#5-operators)
6. [Making Decisions (if/else)](#6-making-decisions-ifelse)
7. [Loops](#7-loops)
8. [Methods (Functions)](#8-methods-functions)
9. [Arrays](#9-arrays)
10. [Strings](#10-strings)

### 🟡 Intermediate
11. [Object-Oriented Programming](#11-object-oriented-programming-oop)
12. [Inheritance & Polymorphism](#12-inheritance--polymorphism)
13. [Interfaces & Abstract Classes](#13-interfaces--abstract-classes)
14. [Collections Framework](#14-collections-framework)
15. [Exception Handling](#15-exception-handling)
16. [File Input & Output](#16-file-input--output)

### 🔴 Advanced
17. [Generics](#17-generics)
18. [Lambdas & Functional Programming](#18-lambdas--functional-programming)
19. [Streams API](#19-streams-api)
20. [Multithreading & Concurrency](#20-multithreading--concurrency)
21. [Modern Java (Java 8 to 21)](#21-modern-java-java-8-to-21)
22. [Minecraft Plugin Basics (Bukkit/Spigot)](#22-minecraft-plugin-basics-bukkitspigot)
23. [Best Practices & Common Mistakes](#26-best-practices--common-mistakes)
24. [Quick Reference Cheat Sheet](#27-quick-reference-cheat-sheet)

### 🎮 Bonus Projects
25. [Making a Terminal-Based Game](#23-making-a-terminal-based-game)
26. [Making UI with Java (Swing)](#24-making-ui-with-java-swing)
27. [Making Animations with Java](#25-making-animations-with-java)

---

# 🟢 BEGINNER

---

## 1. What is Java?

**In simple words:** Java is a programming language designed to be written once and run anywhere. You write your code once and it runs on Windows, Mac, Linux, Android — no changes needed.

**Famous things built with Java:**
- Minecraft (the original game is written in Java)
- Android apps
- Netflix backend
- LinkedIn, Twitter (backend parts)
- Minecraft plugins (Bukkit, Spigot, Paper)

**Java vs other languages:**

| Language | Speed | Where it runs | Famous for |
|----------|-------|---------------|------------|
| Java | Medium-Fast | Everywhere (JVM) | Android, enterprise, Minecraft |
| C++ | Fastest | Native OS | Games, OS, performance |
| Python | Slow | Everywhere | AI, data science, scripting |
| JavaScript | Medium | Browser + Node.js | Web |
| Kotlin | Same as Java | JVM + Android | Modern Android |

**How Java works:**
```
You write code       Compiler compiles       JVM runs it
  (Main.java)   →    to bytecode (.class)  →  on any OS
                         (javac)               (java)
```
This middle step (bytecode) is why Java runs everywhere — the JVM handles OS differences.

**Java versions timeline:**

| Version | Year | Key Features |
|---------|------|--------------|
| Java 8 | 2014 | Lambdas, Streams, Optional — most popular |
| Java 11 | 2018 | LTS, var keyword improvements |
| Java 17 | 2021 | LTS, sealed classes, records |
| Java 21 | 2023 | LTS, virtual threads, pattern matching |

**Install Java:**
```bash
# Download JDK from https://adoptium.net (free, recommended)

# Check if installed:
java -version
javac -version
```

---

## 2. Your First Program

**In Java, everything lives inside a class.**

```java
// File must be named: HelloWorld.java
public class HelloWorld {           // class name must match filename!

    public static void main(String[] args) {  // program starts here
        System.out.println("Hello, World!");  // print with newline
        System.out.print("No newline here");  // print without newline
        System.out.println();                  // just a blank line
    }

}
```

**Line by line:**

| Line | What it means |
|------|---------------|
| `public class HelloWorld` | Define a class named HelloWorld |
| `public static void main(String[] args)` | The entry point — where Java starts |
| `System.out.println(...)` | Print to screen with a newline |
| `System.out.print(...)` | Print without newline |

**Compile and run:**
```bash
javac HelloWorld.java    # compile → creates HelloWorld.class
java HelloWorld          # run (no .java or .class extension!)
```

**Printing different things:**
```java
System.out.println("Text");
System.out.println(42);
System.out.println(3.14);
System.out.println(true);
System.out.println("Sum: " + (3 + 4));   // Sum: 7
```

**Formatted printing:**
```java
String name = "Alice";
int age = 25;
System.out.printf("Name: %s, Age: %d%n", name, age);
// Name: Alice, Age: 25

// Format specifiers:
// %s  = String
// %d  = integer
// %f  = float/double  (%.2f = 2 decimal places)
// %b  = boolean
// %n  = newline (platform-safe alternative to \n)
```

**Comments:**
```java
// Single line comment

/* Multi-line
   comment */

/**
 * Javadoc comment — used for documentation
 * @param name the name to greet
 * @return greeting string
 */
```

---

## 3. Variables & Data Types

**Java has two kinds of types:**
- **Primitive** — simple values stored directly
- **Reference** — objects (stored as references/pointers under the hood)

### Primitive Types

```java
// Integer types
byte  b = 100;           // 1 byte: -128 to 127
short s = 30000;         // 2 bytes: -32,768 to 32,767
int   i = 1000000;       // 4 bytes: most common integer (±2 billion)
long  l = 9999999999L;   // 8 bytes: very large — add L at end!

// Decimal types
float  f = 3.14f;        // 4 bytes: 7 decimal digits — add f at end!
double d = 3.14159265;   // 8 bytes: 15 decimal digits — prefer this

// Other
char    c  = 'A';        // 2 bytes: single character, single quotes
boolean ok = true;       // true or false
```

### Reference Types (Objects)
```java
String  name  = "Alice";       // text — most common reference type
int[]   arr   = {1, 2, 3};    // array
Integer boxed = 42;            // boxed int (object version of int)
```

### Variable naming conventions
```java
// Java convention: camelCase for variables and methods
int playerScore = 0;
String firstName = "Alice";
boolean isGameOver = false;

// Constants: ALL_CAPS with underscores
final int MAX_LIVES = 3;
final double PI = 3.14159;
// final = cannot be changed (like const in C++)
```

### var keyword (Java 10+)
```java
var x = 42;              // compiler infers int
var name = "Alice";      // compiler infers String
var list = new ArrayList<Integer>();  // very useful for long types
```

### Type conversion
```java
// Implicit (widening — safe)
int i = 100;
long l = i;        // int → long: fine, no data loss
double d = i;      // int → double: fine

// Explicit cast (narrowing — may lose data)
double d = 9.99;
int i = (int) d;   // d to int: becomes 9, .99 lost — must cast explicitly

// Parsing strings to numbers
int n    = Integer.parseInt("42");
double x = Double.parseDouble("3.14");
long big = Long.parseLong("999999999999");

// Number to string
String s  = String.valueOf(42);
String s2 = Integer.toString(42);
String s3 = "" + 42;              // quick but not ideal
```

### Wrapper Classes (object versions of primitives)
```java
// Each primitive has a wrapper class:
Integer x = 42;       // int → Integer
Double  d = 3.14;     // double → Double
Boolean b = true;     // boolean → Boolean
Character c = 'A';    // char → Character

// Autoboxing: Java converts automatically
Integer obj = 5;      // auto-boxes int 5 to Integer
int prim = obj;       // auto-unboxes Integer to int

// Useful constants
System.out.println(Integer.MAX_VALUE);  // 2147483647
System.out.println(Integer.MIN_VALUE);  // -2147483648
System.out.println(Double.MAX_VALUE);
```

---

## 4. Getting Input from User

```java
import java.util.Scanner;  // import the Scanner class

public class InputExample {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);  // create Scanner

        System.out.print("Enter your name: ");
        String name = scanner.nextLine();          // read whole line

        System.out.print("Enter your age: ");
        int age = scanner.nextInt();               // read integer

        System.out.println("Hello " + name + ", you are " + age);

        scanner.close();  // good practice — close when done
    }
}
```

### Scanner methods

| Method | Reads |
|--------|-------|
| `nextLine()` | Whole line (String) |
| `next()` | One word (String, stops at whitespace) |
| `nextInt()` | Integer |
| `nextDouble()` | Double |
| `nextLong()` | Long |
| `nextBoolean()` | Boolean (true/false) |

### Common Scanner pitfall
```java
Scanner sc = new Scanner(System.in);

int age = sc.nextInt();
sc.nextLine();              // consume leftover newline — IMPORTANT!
String name = sc.nextLine();  // now reads correctly
```

---

## 5. Operators

### Arithmetic
```java
int a = 10, b = 3;

System.out.println(a + b);   // 13
System.out.println(a - b);   // 7
System.out.println(a * b);   // 30
System.out.println(a / b);   // 3 — integer division!
System.out.println(a % b);   // 1 — remainder

double x = 10.0, y = 3.0;
System.out.println(x / y);   // 3.333...

// Shortcuts
a += 5;   // a = a + 5
a -= 2;   // a = a - 2
a *= 3;   // a = a * 3
a /= 4;   // a = a / 4
a %= 3;   // a = a % 3

// Increment / Decrement
int n = 5;
n++;      // n = 6 (post-increment)
++n;      // n = 7 (pre-increment)
n--;      // n = 6
```

### Comparison (return boolean)
```java
int x = 5, y = 10;
System.out.println(x == y);   // false
System.out.println(x != y);   // true
System.out.println(x < y);    // true
System.out.println(x > y);    // false
System.out.println(x <= 5);   // true
System.out.println(x >= 5);   // true
```

### Logical
```java
boolean a = true, b = false;

System.out.println(a && b);   // false — AND
System.out.println(a || b);   // true  — OR
System.out.println(!a);       // false — NOT

// Short-circuit evaluation
// && stops at first false
// || stops at first true
int x = 5;
if (x != 0 && 10/x > 1) {    // safe: if x==0, second part not evaluated
    System.out.println("ok");
}
```

### String concatenation
```java
String s = "Hello" + " " + "World";  // Hello World
int x = 5;
String msg = "Value: " + x;           // "Value: 5" (auto-converts int)
System.out.println("Sum = " + (3 + 4));  // Sum = 7
System.out.println("Sum = " + 3 + 4);   // Sum = 34 (careful with order!)
```

---

## 6. Making Decisions (if/else)

### if / else if / else
```java
int score = 75;

if (score >= 90) {
    System.out.println("Grade: A");
} else if (score >= 80) {
    System.out.println("Grade: B");
} else if (score >= 70) {
    System.out.println("Grade: C");
} else if (score >= 60) {
    System.out.println("Grade: D");
} else {
    System.out.println("Grade: F");
}
```

### switch
```java
int day = 3;
switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    case 6:
    case 7:
        System.out.println("Weekend!");
        break;
    default:
        System.out.println("Unknown");
}

// Switch expression (Java 14+) — cleaner
String result = switch (day) {
    case 1 -> "Monday";
    case 2 -> "Tuesday";
    case 3 -> "Wednesday";
    case 6, 7 -> "Weekend";
    default -> "Unknown";
};
```

### Ternary
```java
int age = 20;
String status = (age >= 18) ? "adult" : "minor";
System.out.println(status);  // adult

int a = 5, b = 9;
int max = (a > b) ? a : b;  // 9
```

---

## 7. Loops

### while
```java
int i = 1;
while (i <= 5) {
    System.out.print(i + " ");
    i++;
}
// Output: 1 2 3 4 5

// User input validation
Scanner sc = new Scanner(System.in);
int num;
do {
    System.out.print("Enter positive number: ");
    num = sc.nextInt();
} while (num <= 0);
```

### for
```java
for (int i = 0; i < 5; i++) {
    System.out.print(i + " ");
}
// Output: 0 1 2 3 4

// Backwards
for (int i = 10; i >= 1; i--) {
    System.out.print(i + " ");
}

// Even numbers
for (int i = 0; i <= 20; i += 2) {
    System.out.print(i + " ");
}
```

### for-each — iterate over arrays and collections
```java
int[] numbers = {10, 20, 30, 40, 50};
for (int num : numbers) {
    System.out.println(num);
}

String[] fruits = {"apple", "banana", "cherry"};
for (String fruit : fruits) {
    System.out.println(fruit.toUpperCase());
}
```

### break and continue
```java
// break: exit loop
for (int i = 0; i < 10; i++) {
    if (i == 5) break;
    System.out.print(i + " ");
}
// Output: 0 1 2 3 4

// continue: skip to next iteration
for (int i = 0; i < 10; i++) {
    if (i % 2 == 0) continue;
    System.out.print(i + " ");
}
// Output: 1 3 5 7 9
```

---

## 8. Methods (Functions)

**In Java, functions are called "methods" and must live inside a class.**

```java
public class Calculator {

    // Return type → method name → parameters
    public static int add(int a, int b) {
        return a + b;
    }

    public static double multiply(double a, double b) {
        return a * b;
    }

    // void = returns nothing
    public static void printLine() {
        System.out.println("─────────────");
    }

    public static void greet(String name) {
        System.out.println("Hello, " + name + "!");
    }

    public static void main(String[] args) {
        int result = add(3, 4);
        System.out.println(result);   // 7

        System.out.println(add(10, 20));     // 30
        System.out.println(multiply(2.5, 4.0)); // 10.0

        printLine();
        greet("Alice");
    }
}
```

### Method overloading — same name, different parameters
```java
public static void print(int x) {
    System.out.println("Integer: " + x);
}
public static void print(double x) {
    System.out.println("Double: " + x);
}
public static void print(String x) {
    System.out.println("String: " + x);
}

print(42);       // Integer: 42
print(3.14);     // Double: 3.14
print("hello");  // String: hello
```

### Varargs — variable number of arguments
```java
public static int sum(int... numbers) {
    int total = 0;
    for (int n : numbers) total += n;
    return total;
}

System.out.println(sum(1, 2, 3));          // 6
System.out.println(sum(1, 2, 3, 4, 5));   // 15
System.out.println(sum(10));               // 10
```

### Recursion
```java
public static int factorial(int n) {
    if (n == 0 || n == 1) return 1;   // base case
    return n * factorial(n - 1);
}

public static int fibonacci(int n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

System.out.println(factorial(5));    // 120
System.out.println(fibonacci(10));   // 55
```

---

## 9. Arrays

**Fixed-size container for same-type elements. Index starts at 0.**

```java
// Declare and initialize
int[] scores = {90, 85, 78, 92, 88};

// Or declare then fill
int[] arr = new int[5];   // creates array of 5 zeros
arr[0] = 10;
arr[1] = 20;

// Access
System.out.println(scores[0]);  // 90 (first)
System.out.println(scores[4]);  // 88 (last)

// Length
System.out.println(scores.length);  // 5 (not length()!)

// Loop through
for (int i = 0; i < scores.length; i++) {
    System.out.println("Score " + i + ": " + scores[i]);
}

// For-each loop
for (int score : scores) {
    System.out.println(score);
}
```

### Useful Arrays methods
```java
import java.util.Arrays;

int[] arr = {5, 3, 1, 4, 2};

Arrays.sort(arr);                       // sort: {1, 2, 3, 4, 5}
System.out.println(Arrays.toString(arr)); // [1, 2, 3, 4, 5]

int idx = Arrays.binarySearch(arr, 3);  // find index of 3 (array must be sorted)

int[] copy = Arrays.copyOf(arr, arr.length);  // copy array
Arrays.fill(arr, 0);                    // fill all with 0
```

### 2D Arrays
```java
int[][] grid = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

System.out.println(grid[1][2]);  // 6 (row 1, col 2)

// Loop 2D array
for (int i = 0; i < grid.length; i++) {
    for (int j = 0; j < grid[i].length; j++) {
        System.out.print(grid[i][j] + " ");
    }
    System.out.println();
}
```

---

## 10. Strings

**String is a class in Java, not a primitive.**

```java
String s = "Hello, World!";

// Length
System.out.println(s.length());         // 13

// Character at index
System.out.println(s.charAt(0));        // H
System.out.println(s.charAt(7));        // W

// Substring
System.out.println(s.substring(7));        // World! (from index 7 to end)
System.out.println(s.substring(7, 12));    // World (from 7, up to not including 12)

// Search
System.out.println(s.indexOf("World"));    // 7 (-1 if not found)
System.out.println(s.contains("Hello"));   // true
System.out.println(s.startsWith("Hello")); // true
System.out.println(s.endsWith("!"));       // true

// Modify (strings are immutable — returns new string)
System.out.println(s.toUpperCase());       // HELLO, WORLD!
System.out.println(s.toLowerCase());       // hello, world!
System.out.println(s.replace("World", "Java"));  // Hello, Java!
System.out.println(s.trim());              // removes leading/trailing spaces

// Split
String csv = "apple,banana,cherry";
String[] fruits = csv.split(",");          // ["apple", "banana", "cherry"]

// Compare — NEVER use == for strings!
String a = "hello";
String b = "hello";
System.out.println(a == b);          // might be true or false (compares addresses)
System.out.println(a.equals(b));     // true — always use .equals()!
System.out.println(a.equalsIgnoreCase("HELLO"));  // true

// isEmpty and isBlank
System.out.println("".isEmpty());    // true
System.out.println("  ".isBlank()); // true (Java 11+)

// Repeat (Java 11+)
System.out.println("ha".repeat(3));  // hahaha
```

### StringBuilder — efficient string building
```java
// Bad (slow): creates new String object every time
String result = "";
for (int i = 0; i < 1000; i++) {
    result += i;    // creates 1000 new String objects!
}

// Good: StringBuilder modifies in place
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i);
}
String result = sb.toString();

// Other StringBuilder methods
sb.insert(0, "START: ");
sb.delete(0, 6);
sb.reverse();
sb.replace(0, 4, "XXXX");
System.out.println(sb.length());
```

---

# 🟡 INTERMEDIATE

---

## 11. Object-Oriented Programming (OOP)

**Java is built entirely around OOP. Everything is an object (almost).**

### Class and Object
```java
public class Dog {
    // Fields (properties/attributes)
    private String name;    // private = only accessible inside Dog
    private String breed;
    private int age;

    // Constructor — creates an object
    public Dog(String name, String breed, int age) {
        this.name  = name;    // this.name = field, name = parameter
        this.breed = breed;
        this.age   = age;
    }

    // Methods (behavior)
    public void bark() {
        System.out.println(name + " says: Woof!");
    }

    public void introduce() {
        System.out.println("I'm " + name + ", a " + breed + ", age " + age);
    }

    // Getters — read private fields
    public String getName()  { return name; }
    public int    getAge()   { return age; }
    public String getBreed() { return breed; }

    // Setters — write private fields (with validation)
    public void setAge(int age) {
        if (age >= 0 && age <= 30) this.age = age;
    }

    // toString — called when you print the object
    @Override
    public String toString() {
        return "Dog{name=" + name + ", breed=" + breed + ", age=" + age + "}";
    }
}
```

**Using the class:**
```java
Dog d1 = new Dog("Rex", "Husky", 3);
Dog d2 = new Dog("Buddy", "Labrador", 5);

d1.bark();          // Rex says: Woof!
d2.introduce();     // I'm Buddy, a Labrador, age 5

System.out.println(d1);  // calls toString(): Dog{name=Rex, ...}
System.out.println(d1.getName());  // Rex

d1.setAge(4);
System.out.println(d1.getAge());   // 4
```

### Multiple constructors
```java
public class Point {
    double x, y;

    // Default constructor
    public Point() {
        this.x = 0;
        this.y = 0;
    }

    // Parameterized constructor
    public Point(double x, double y) {
        this.x = x;
        this.y = y;
    }

    // Constructor chaining with this()
    public Point(double val) {
        this(val, val);    // calls Point(double x, double y)
    }

    public double distanceTo(Point other) {
        double dx = this.x - other.x;
        double dy = this.y - other.y;
        return Math.sqrt(dx*dx + dy*dy);
    }

    @Override
    public String toString() {
        return "(" + x + ", " + y + ")";
    }
}

Point p1 = new Point(3, 4);
Point p2 = new Point();
System.out.println(p1.distanceTo(p2));  // 5.0
```

### Static members — shared by all instances
```java
public class Counter {
    private int id;
    private static int count = 0;  // one copy for ALL Counter objects

    public Counter() {
        count++;
        this.id = count;
    }

    public static int getCount() { return count; }
    public int getId() { return id; }
}

Counter c1 = new Counter();
Counter c2 = new Counter();
Counter c3 = new Counter();
System.out.println(Counter.getCount());  // 3
System.out.println(c1.getId());  // 1
System.out.println(c2.getId());  // 2
```

### Records (Java 14+) — concise data classes
```java
// Old way (lots of boilerplate)
public class PersonOld {
    private final String name;
    private final int age;
    // constructor, getters, equals, hashCode, toString...
}

// New way with record — generates everything automatically!
public record Person(String name, int age) {}

// Usage
Person p = new Person("Alice", 25);
System.out.println(p.name());  // Alice
System.out.println(p.age());   // 25
System.out.println(p);         // Person[name=Alice, age=25]
```

---

## 12. Inheritance & Polymorphism

```java
// Parent class
public class Animal {
    protected String name;
    protected int age;

    public Animal(String name, int age) {
        this.name = name;
        this.age  = age;
    }

    public void breathe() {
        System.out.println(name + " is breathing");
    }

    // Can be overridden by child classes
    public void speak() {
        System.out.println(name + " makes a sound");
    }

    @Override
    public String toString() {
        return name + " (age " + age + ")";
    }
}

// Child class — inherits from Animal
public class Dog extends Animal {
    private String breed;

    public Dog(String name, int age, String breed) {
        super(name, age);    // call parent constructor — must be first line!
        this.breed = breed;
    }

    @Override
    public void speak() {
        System.out.println(name + " barks: Woof!");
    }

    public void fetch() {
        System.out.println(name + " fetches the ball!");
    }
}

public class Cat extends Animal {
    public Cat(String name, int age) {
        super(name, age);
    }

    @Override
    public void speak() {
        System.out.println(name + " meows: Meow!");
    }
}
```

### Polymorphism
```java
Animal[] animals = {
    new Animal("Generic", 1),
    new Dog("Rex", 3, "Husky"),
    new Cat("Luna", 2)
};

for (Animal a : animals) {
    a.speak();   // calls correct version based on ACTUAL type!
}
// Output:
// Generic makes a sound
// Rex barks: Woof!
// Luna meows: Meow!

// instanceof — check actual type
Animal a = new Dog("Rex", 3, "Husky");
if (a instanceof Dog dog) {        // Java 16+ pattern matching
    dog.fetch();                   // can call Dog-specific methods
}
```

### super — calling parent methods
```java
public class Dog extends Animal {

    @Override
    public void speak() {
        super.speak();   // call parent's speak() first
        System.out.println(name + " also barks!");
    }
}
```

### final — prevent extension or override
```java
public final class MathHelper { }   // can't extend this class

public class Animal {
    public final void breathe() { }  // can't override this method
}
```

---

## 13. Interfaces & Abstract Classes

### Abstract class — partially implemented base
```java
// Cannot be instantiated directly
public abstract class Shape {
    protected String color;

    public Shape(String color) {
        this.color = color;
    }

    // Abstract method — MUST be implemented by child
    public abstract double area();
    public abstract double perimeter();

    // Concrete method — available to all children
    public void describe() {
        System.out.printf("%s %s: area=%.2f, perimeter=%.2f%n",
            color, getClass().getSimpleName(), area(), perimeter());
    }
}

public class Circle extends Shape {
    private double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override public double area()      { return Math.PI * radius * radius; }
    @Override public double perimeter() { return 2 * Math.PI * radius; }
}

public class Rectangle extends Shape {
    private double width, height;

    public Rectangle(String color, double w, double h) {
        super(color); this.width = w; this.height = h;
    }

    @Override public double area()      { return width * height; }
    @Override public double perimeter() { return 2 * (width + height); }
}

Circle    c = new Circle("Red", 5);
Rectangle r = new Rectangle("Blue", 4, 6);
c.describe();   // Red Circle: area=78.54, perimeter=31.42
r.describe();   // Blue Rectangle: area=24.00, perimeter=20.00
```

### Interface — a pure contract
```java
// Interface: defines WHAT something can do, not HOW
public interface Flyable {
    void fly();             // implicitly public abstract
    default void land() {   // default method (Java 8+) — has implementation
        System.out.println("Landing...");
    }
}

public interface Swimmable {
    void swim();
}

// A class can implement multiple interfaces (unlike extends)
public class Duck extends Animal implements Flyable, Swimmable {
    public Duck(String name) { super(name, 1); }

    @Override public void fly()  { System.out.println(name + " is flying!"); }
    @Override public void swim() { System.out.println(name + " is swimming!"); }
    @Override public void speak(){ System.out.println(name + " quacks!"); }
}

Duck d = new Duck("Donald");
d.fly();     // Donald is flying!
d.swim();    // Donald is swimming!
d.land();    // Landing... (from default method)
```

### Key difference

| | Abstract Class | Interface |
|---|----------------|-----------|
| Can have fields | Yes | Only constants |
| Can have constructor | Yes | No |
| Can extend | One only | Multiple |
| Use for | Shared base with state | Capability contracts |

### Functional interfaces (Java 8+)
```java
@FunctionalInterface
public interface Transformer {
    int transform(int value);   // exactly one abstract method
}

// Can be used with lambdas
Transformer doubler = value -> value * 2;
Transformer squarer = value -> value * value;

System.out.println(doubler.transform(5));   // 10
System.out.println(squarer.transform(5));   // 25
```

---

## 14. Collections Framework

**Java's built-in data structures — all in `java.util`.**

### List — ordered, allows duplicates

```java
import java.util.*;

// ArrayList — dynamic array (fast random access)
List<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
names.add("Charlie");
names.add("Alice");    // duplicates allowed

System.out.println(names.get(1));     // Bob
System.out.println(names.size());     // 4
System.out.println(names.contains("Alice")); // true

names.remove("Bob");          // remove by value
names.remove(0);              // remove by index

names.set(0, "Dave");         // replace at index

Collections.sort(names);      // sort alphabetically
Collections.reverse(names);   // reverse order

for (String name : names) {
    System.out.println(name);
}

// LinkedList — fast insert/remove at front and back
List<Integer> linked = new LinkedList<>();
((LinkedList<Integer>) linked).addFirst(1);
((LinkedList<Integer>) linked).addLast(2);
```

### Map — key-value pairs
```java
// HashMap — fast, unordered
Map<String, Integer> scores = new HashMap<>();
scores.put("Alice", 95);
scores.put("Bob", 87);
scores.put("Charlie", 92);

System.out.println(scores.get("Alice"));         // 95
System.out.println(scores.getOrDefault("Dave", 0)); // 0 (not found)
System.out.println(scores.containsKey("Bob"));   // true

scores.remove("Bob");
System.out.println(scores.size());  // 2

// Iterate
for (Map.Entry<String, Integer> entry : scores.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}

// Shorthand
scores.forEach((name, score) -> System.out.println(name + ": " + score));

// TreeMap — sorted by key
Map<String, Integer> sorted = new TreeMap<>(scores);  // auto-sorted alphabetically
```

### Set — unique elements, no duplicates
```java
// HashSet — unordered, fast lookup
Set<String> unique = new HashSet<>();
unique.add("apple");
unique.add("banana");
unique.add("apple");   // ignored — already exists
unique.add("cherry");

System.out.println(unique.size());            // 3
System.out.println(unique.contains("apple")); // true

// TreeSet — sorted
Set<Integer> sortedSet = new TreeSet<>();
sortedSet.add(5); sortedSet.add(2); sortedSet.add(8); sortedSet.add(1);
System.out.println(sortedSet);  // [1, 2, 5, 8] — always sorted
```

### Queue and Stack
```java
// Queue (FIFO)
Queue<String> queue = new LinkedList<>();
queue.offer("Alice");
queue.offer("Bob");
queue.offer("Charlie");

System.out.println(queue.peek());   // Alice (look at front)
System.out.println(queue.poll());   // Alice (remove and return front)
System.out.println(queue.peek());   // Bob

// Stack (LIFO) — use Deque in modern Java
Deque<Integer> stack = new ArrayDeque<>();
stack.push(10); stack.push(20); stack.push(30);
System.out.println(stack.peek());   // 30
System.out.println(stack.pop());    // 30 (remove top)

// PriorityQueue — smallest element first
PriorityQueue<Integer> pq = new PriorityQueue<>();
pq.offer(5); pq.offer(1); pq.offer(9); pq.offer(3);
while (!pq.isEmpty()) {
    System.out.print(pq.poll() + " ");  // 1 3 5 9
}
```

### Collections utility methods
```java
List<Integer> nums = new ArrayList<>(Arrays.asList(3, 1, 4, 1, 5, 9));

Collections.sort(nums);                    // [1, 1, 3, 4, 5, 9]
Collections.sort(nums, Collections.reverseOrder());  // [9, 5, 4, 3, 1, 1]
Collections.reverse(nums);
Collections.shuffle(nums);                 // random order
Collections.max(nums);                     // maximum
Collections.min(nums);                     // minimum
Collections.frequency(nums, 1);           // count occurrences of 1
```

---

## 15. Exception Handling

### try-catch-finally
```java
public class Division {
    public static double divide(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException("Cannot divide by zero!");
        }
        return (double) a / b;
    }

    public static void main(String[] args) {
        try {
            System.out.println(divide(10, 2));   // 5.0
            System.out.println(divide(10, 0));   // throws exception
        } catch (ArithmeticException e) {
            System.out.println("Math error: " + e.getMessage());
        } catch (Exception e) {
            System.out.println("Unknown error: " + e.getMessage());
        } finally {
            // ALWAYS runs — whether exception or not
            System.out.println("Execution finished.");
        }
    }
}
```

### Common exception types

| Exception | When it happens |
|-----------|----------------|
| `NullPointerException` | Using null reference |
| `ArrayIndexOutOfBoundsException` | Invalid array index |
| `NumberFormatException` | Parsing "abc" as number |
| `ClassCastException` | Invalid type cast |
| `ArithmeticException` | Math error (div by zero) |
| `StackOverflowError` | Infinite recursion |
| `IOException` | File/network I/O error |

### Checked vs Unchecked exceptions
```java
// Checked: must handle or declare with throws
// Usually for external problems (file not found, network, etc.)
public void readFile(String path) throws IOException {
    // ...
}

// Unchecked (RuntimeException): optional to catch
// Usually for programmer errors (null pointer, bad index, etc.)
```

### Custom exception
```java
public class InsufficientBalanceException extends RuntimeException {
    private double amount;

    public InsufficientBalanceException(double amount) {
        super("Cannot withdraw $" + amount + " — insufficient balance");
        this.amount = amount;
    }

    public double getAmount() { return amount; }
}

// Usage:
try {
    throw new InsufficientBalanceException(500.0);
} catch (InsufficientBalanceException e) {
    System.out.println(e.getMessage());
    System.out.println("Attempted: " + e.getAmount());
}
```

### try-with-resources (auto-close)
```java
// Automatically closes resources — no need for finally
try (Scanner sc = new Scanner(new File("input.txt"))) {
    while (sc.hasNextLine()) {
        System.out.println(sc.nextLine());
    }
}  // scanner closed automatically here, even if exception thrown
```

---

## 16. File Input & Output

### Writing to a file
```java
import java.io.*;
import java.nio.file.*;

// Modern way (Java NIO — recommended)
String content = "Line 1\nLine 2\nLine 3";
Files.writeString(Path.of("output.txt"), content);

// Write list of lines
List<String> lines = List.of("Hello", "World", "Java");
Files.write(Path.of("output.txt"), lines);

// Append
Files.writeString(Path.of("output.txt"), "\nNew line", StandardOpenOption.APPEND);
```

### Reading from a file
```java
// Read all lines at once
List<String> lines = Files.readAllLines(Path.of("input.txt"));
for (String line : lines) {
    System.out.println(line);
}

// Read entire file as string
String content = Files.readString(Path.of("input.txt"));

// Traditional BufferedReader (more control)
try (BufferedReader br = new BufferedReader(new FileReader("input.txt"))) {
    String line;
    while ((line = br.readLine()) != null) {
        System.out.println(line);
    }
}
```

### Writing with BufferedWriter
```java
try (BufferedWriter bw = new BufferedWriter(new FileWriter("output.txt"))) {
    bw.write("Hello, File!");
    bw.newLine();
    bw.write("Second line");
}  // auto-closed
```

---

# 🔴 ADVANCED

---

## 17. Generics

**Write code that works with any type — safely.**

```java
// Without generics — unsafe
List list = new ArrayList();
list.add("hello");
list.add(42);           // compiles but...
String s = (String) list.get(1);  // ClassCastException at runtime!

// With generics — type-safe
List<String> strList = new ArrayList<>();
strList.add("hello");
// strList.add(42);    // compile error — caught early!
String s = strList.get(0);  // no cast needed
```

### Generic methods
```java
public static <T> T getFirst(List<T> list) {
    if (list.isEmpty()) return null;
    return list.get(0);
}

public static <T extends Comparable<T>> T maximum(T a, T b) {
    return a.compareTo(b) >= 0 ? a : b;
}

System.out.println(maximum(3, 7));           // 7
System.out.println(maximum(3.5, 2.1));       // 3.5
System.out.println(maximum("apple", "zoo")); // zoo
```

### Generic class
```java
public class Box<T> {
    private T content;

    public Box(T content) { this.content = content; }
    public T get()        { return content; }
    public void set(T val){ this.content = val; }

    @Override
    public String toString() { return "Box[" + content + "]"; }
}

Box<Integer> intBox = new Box<>(42);
Box<String> strBox  = new Box<>("hello");

System.out.println(intBox.get());  // 42
System.out.println(strBox);        // Box[hello]
```

### Wildcards
```java
// ? = any type
public static void printList(List<?> list) {
    for (Object item : list) {
        System.out.println(item);
    }
}

// ? extends T = T or any subtype of T (upper bound)
public static double sum(List<? extends Number> list) {
    double total = 0;
    for (Number n : list) total += n.doubleValue();
    return total;
}

System.out.println(sum(List.of(1, 2, 3)));        // works with Integer
System.out.println(sum(List.of(1.1, 2.2, 3.3)));  // works with Double
```

---

## 18. Lambdas & Functional Programming

**Lambdas let you write functions inline without naming them.**

```java
// Old way — anonymous class
Runnable r = new Runnable() {
    @Override
    public void run() {
        System.out.println("Running!");
    }
};

// Lambda way — much cleaner
Runnable r = () -> System.out.println("Running!");

r.run();  // Running!
```

### Lambda syntax
```java
// No params
() -> System.out.println("Hello")

// One param (parentheses optional)
x -> x * 2
(x) -> x * 2

// Multiple params
(a, b) -> a + b

// Block body
(a, b) -> {
    int result = a + b;
    return result;
}
```

### Built-in functional interfaces
```java
import java.util.function.*;

// Function<T, R> — takes T, returns R
Function<String, Integer> strLen = s -> s.length();
System.out.println(strLen.apply("Hello"));  // 5

// Predicate<T> — takes T, returns boolean
Predicate<Integer> isEven = n -> n % 2 == 0;
System.out.println(isEven.test(4));   // true
System.out.println(isEven.test(5));   // false

// Consumer<T> — takes T, returns nothing
Consumer<String> printer = s -> System.out.println(">> " + s);
printer.accept("hello");   // >> hello

// Supplier<T> — takes nothing, returns T
Supplier<Double> random = () -> Math.random();
System.out.println(random.get());

// BiFunction<T, U, R> — takes two inputs, returns R
BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;
System.out.println(add.apply(3, 4));   // 7
```

### Method references — even shorter lambdas
```java
// Instead of: s -> System.out.println(s)
// Use:        System.out::println

List<String> names = List.of("Alice", "Bob", "Charlie");
names.forEach(System.out::println);   // method reference

// Static method reference
Function<String, Integer> parser = Integer::parseInt;
System.out.println(parser.apply("42"));   // 42

// Instance method reference
String prefix = "Hello, ";
Function<String, String> greeter = prefix::concat;
System.out.println(greeter.apply("Alice"));   // Hello, Alice

// Constructor reference
Supplier<ArrayList<String>> listMaker = ArrayList::new;
ArrayList<String> list = listMaker.get();
```

---

## 19. Streams API

**Process collections in a functional, pipeline style.**

```java
import java.util.stream.*;

List<Integer> numbers = List.of(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

// Pipeline: source → intermediate ops → terminal op
int sum = numbers.stream()
    .filter(n -> n % 2 == 0)    // keep even: 2, 4, 6, 8, 10
    .map(n -> n * n)             // square: 4, 16, 36, 64, 100
    .reduce(0, Integer::sum);    // sum: 220

System.out.println(sum);  // 220
```

### Common stream operations
```java
List<String> names = List.of("Alice", "Bob", "Charlie", "Dave", "Anna");

// filter — keep matching
names.stream()
    .filter(s -> s.startsWith("A"))
    .forEach(System.out::println);  // Alice, Anna

// map — transform
names.stream()
    .map(String::toUpperCase)
    .forEach(System.out::println);

// sorted
names.stream()
    .sorted()
    .forEach(System.out::println);

// collect to new list
List<String> aNames = names.stream()
    .filter(s -> s.startsWith("A"))
    .collect(Collectors.toList());

// count
long count = names.stream()
    .filter(s -> s.length() > 4)
    .count();  // 3 (Alice, Charlie, Anna is 4... Bob is 3)

// anyMatch, allMatch, noneMatch
boolean hasAlice = names.stream().anyMatch(s -> s.equals("Alice"));  // true
boolean allLong  = names.stream().allMatch(s -> s.length() > 2);     // true
boolean noneEmpty= names.stream().noneMatch(String::isEmpty);         // true

// findFirst
Optional<String> first = names.stream()
    .filter(s -> s.contains("har"))
    .findFirst();
System.out.println(first.orElse("not found"));  // Charlie

// min and max
Optional<String> shortest = names.stream()
    .min(Comparator.comparingInt(String::length));
System.out.println(shortest.get());   // Bob

// groupingBy
Map<Integer, List<String>> byLength = names.stream()
    .collect(Collectors.groupingBy(String::length));
// {3=[Bob], 4=[Dave, Anna], 5=[Alice], 7=[Charlie]}

// joining
String joined = names.stream()
    .collect(Collectors.joining(", ", "[", "]"));
System.out.println(joined);  // [Alice, Bob, Charlie, Dave, Anna]
```

---

## 20. Multithreading & Concurrency

### Creating threads
```java
// Method 1: extend Thread
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Thread running: " + getName());
    }
}

MyThread t = new MyThread();
t.start();   // start() — don't call run() directly!

// Method 2: implement Runnable (preferred)
Runnable task = () -> {
    System.out.println("Task running in: " + Thread.currentThread().getName());
};
Thread thread = new Thread(task);
thread.start();
```

### ExecutorService — thread pool
```java
import java.util.concurrent.*;

// Thread pool — reuse threads, don't create new ones each time
ExecutorService executor = Executors.newFixedThreadPool(4);  // 4 worker threads

for (int i = 0; i < 10; i++) {
    final int taskNum = i;
    executor.submit(() -> {
        System.out.println("Task " + taskNum + " on " + Thread.currentThread().getName());
    });
}

executor.shutdown();          // no more new tasks
executor.awaitTermination(5, TimeUnit.SECONDS);  // wait for all to finish
```

### synchronized — prevent race conditions
```java
public class BankAccount {
    private double balance = 1000;

    // Only one thread can execute this at a time
    public synchronized void withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
            System.out.println("Withdrew: " + amount + ", Balance: " + balance);
        }
    }

    public synchronized double getBalance() { return balance; }
}
```

### Future and Callable — get results from threads
```java
ExecutorService executor = Executors.newSingleThreadExecutor();

Callable<Integer> task = () -> {
    Thread.sleep(2000);  // simulate work
    return 42;
};

Future<Integer> future = executor.submit(task);

// Do other work...
System.out.println("Waiting for result...");

int result = future.get();  // blocks until result is ready
System.out.println("Result: " + result);  // 42

executor.shutdown();
```

### CompletableFuture (Java 8+) — modern async
```java
import java.util.concurrent.CompletableFuture;

CompletableFuture<String> future = CompletableFuture
    .supplyAsync(() -> "Hello")           // runs in background
    .thenApply(s -> s + " World")         // transform result
    .thenApply(String::toUpperCase);       // transform again

System.out.println(future.get());   // HELLO WORLD

// Chain multiple async tasks
CompletableFuture.supplyAsync(() -> fetchUser(1))
    .thenCompose(user -> fetchOrders(user.getId()))
    .thenAccept(orders -> System.out.println("Orders: " + orders))
    .exceptionally(e -> { System.out.println("Error: " + e); return null; });
```

---

## 21. Modern Java (Java 8 to 21)

### Optional — avoid NullPointerException
```java
import java.util.Optional;

Optional<String> findUser(int id) {
    if (id == 1) return Optional.of("Alice");
    return Optional.empty();
}

Optional<String> user = findUser(1);
user.ifPresent(u -> System.out.println("Found: " + u));   // Found: Alice

String name = user.orElse("Unknown");              // get or default
String name2 = user.orElseGet(() -> "Computed");  // lazy default
String name3 = user.orElseThrow(() -> new RuntimeException("No user")); // or throw

Optional<String> missing = findUser(99);
System.out.println(missing.isPresent());  // false
System.out.println(missing.isEmpty());    // true
```

### var — local variable type inference (Java 10+)
```java
var list = new ArrayList<String>();      // ArrayList<String>
var map  = new HashMap<String, Integer>(); // HashMap<String, Integer>
var name = "Alice";                      // String

// Useful in for loops
for (var entry : map.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
```

### Text blocks (Java 15+) — multi-line strings
```java
String html = """
        <html>
            <body>
                <h1>Hello</h1>
            </body>
        </html>
        """;

String json = """
        {
            "name": "Alice",
            "age": 25
        }
        """;
System.out.println(json);
```

### Sealed classes (Java 17+) — restrict who can extend
```java
public sealed class Shape permits Circle, Rectangle, Triangle {}

public final class Circle extends Shape {
    double radius;
    Circle(double r) { this.radius = r; }
}

public final class Rectangle extends Shape {
    double width, height;
    Rectangle(double w, double h) { width=w; height=h; }
}

// Now only Circle, Rectangle, and Triangle can extend Shape
```

### Pattern matching (Java 16+)
```java
Object obj = "Hello";

// Old way
if (obj instanceof String) {
    String s = (String) obj;
    System.out.println(s.length());
}

// New way (pattern matching instanceof)
if (obj instanceof String s) {       // declares s automatically
    System.out.println(s.length());  // can use s directly!
}

// With switch (Java 21)
String result = switch (obj) {
    case Integer i -> "Integer: " + i;
    case String  s -> "String: " + s.toUpperCase();
    case null      -> "null";
    default        -> "Other: " + obj;
};
```

---

## 22. Minecraft Plugin Basics (Bukkit/Spigot)

**This is why many people learn Java! Minecraft plugins let you modify server behavior.**

### Setup
```
1. Download Paper/Spigot server jar
2. Add Spigot API dependency to your project (Maven or Gradle)
3. Create plugin.yml
4. Create main class extending JavaPlugin
```

**pom.xml (Maven) dependency:**
```xml
<dependency>
    <groupId>org.spigotmc</groupId>
    <artifactId>spigot-api</artifactId>
    <version>1.21.1-R0.1-SNAPSHOT</version>
    <scope>provided</scope>
</dependency>
```

**plugin.yml:**
```yaml
name: MyPlugin
version: 1.0
main: com.yourname.myplugin.MyPlugin
api-version: 1.21
description: My first Minecraft plugin
```

### Main plugin class
```java
package com.yourname.myplugin;

import org.bukkit.plugin.java.JavaPlugin;

public class MyPlugin extends JavaPlugin {

    @Override
    public void onEnable() {
        // runs when plugin loads
        getLogger().info("MyPlugin has been enabled!");

        // Register commands
        getCommand("hello").setExecutor(new HelloCommand());

        // Register events
        getServer().getPluginManager().registerEvents(new PlayerListener(), this);
    }

    @Override
    public void onDisable() {
        // runs when plugin unloads / server stops
        getLogger().info("MyPlugin has been disabled!");
    }
}
```

### Creating a command
```java
import org.bukkit.command.*;
import org.bukkit.entity.Player;

public class HelloCommand implements CommandExecutor {

    @Override
    public boolean onCommand(CommandSender sender, Command cmd,
                             String label, String[] args) {

        if (!(sender instanceof Player player)) {
            sender.sendMessage("Only players can use this command!");
            return true;
        }

        player.sendMessage("§aHello, " + player.getName() + "!");
        // § + color code = colored text

        if (args.length > 0) {
            player.sendMessage("You said: " + args[0]);
        }

        return true;   // return true = command succeeded
    }
}
```

**plugin.yml command section:**
```yaml
commands:
  hello:
    description: Say hello
    usage: /hello [message]
    permission: myplugin.hello
```

### Listening to events
```java
import org.bukkit.event.*;
import org.bukkit.event.player.*;
import org.bukkit.event.block.*;

public class PlayerListener implements Listener {

    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event) {
        Player player = event.getPlayer();
        event.setJoinMessage("§e" + player.getName() + " joined the game!");

        // Give player 5 apples
        player.getInventory().addItem(
            new ItemStack(Material.APPLE, 5)
        );
    }

    @EventHandler
    public void onPlayerChat(AsyncPlayerChatEvent event) {
        Player player = event.getPlayer();
        String message = event.getMessage();

        // Block bad words
        if (message.contains("badword")) {
            event.setCancelled(true);
            player.sendMessage("§cWatch your language!");
        }
    }

    @EventHandler
    public void onBlockBreak(BlockBreakEvent event) {
        Player player = event.getPlayer();
        Block block = event.getBlock();

        // Log when players break blocks
        Bukkit.getLogger().info(player.getName() +
            " broke " + block.getType() + " at " + block.getLocation());
    }
}
```

### Working with players
```java
Player player = ...; // get from event or Bukkit.getPlayer("name")

// Location
Location loc = player.getLocation();
double x = loc.getX(), y = loc.getY(), z = loc.getZ();
player.teleport(new Location(player.getWorld(), 0, 64, 0));

// Inventory
player.getInventory().addItem(new ItemStack(Material.DIAMOND, 64));
player.getInventory().clear();

// Health and food
player.setHealth(20.0);    // max health
player.setFoodLevel(20);

// Game mode
player.setGameMode(GameMode.CREATIVE);

// Send messages
player.sendMessage("§6Hello §aWorld!");   // colored
player.sendTitle("§6Welcome!", "§eTo the server", 10, 70, 20);

// Permissions
if (player.hasPermission("myplugin.admin")) {
    // admin stuff
}
```

### Scheduling tasks
```java
// Run once after 20 ticks (1 second = 20 ticks)
Bukkit.getScheduler().runTaskLater(plugin, () -> {
    Bukkit.broadcastMessage("§e5 seconds passed!");
}, 100L);   // 100 ticks = 5 seconds

// Repeat every second
Bukkit.getScheduler().runTaskTimer(plugin, () -> {
    // this runs every 20 ticks
}, 0L, 20L);   // delay=0, period=20

// Async (don't use Bukkit API inside async!)
Bukkit.getScheduler().runTaskAsynchronously(plugin, () -> {
    // database queries, web requests, file I/O here
});
```

### Bukkit color codes
```
§0 Black        §8 Dark Gray
§1 Dark Blue    §9 Blue
§2 Dark Green   §a Green
§3 Dark Aqua    §b Aqua
§4 Dark Red     §c Red
§5 Dark Purple  §d Light Purple
§6 Gold         §e Yellow
§7 Gray         §f White

§l Bold    §o Italic    §n Underline    §m Strikethrough    §r Reset
```

---

## 23. Making a Terminal-Based Game

Terminal games use the console for input/output — no graphics library needed. A classic starting project is a **text adventure** or **number guessing game**.

### Example: Number Guessing Game

```java
import java.util.Scanner;
import java.util.Random;

public class GuessingGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int secretNumber = random.nextInt(100) + 1;  // 1 to 100
        int attempts = 0;
        boolean won = false;

        System.out.println("=== Number Guessing Game ===");
        System.out.println("Guess a number between 1 and 100!\n");

        while (!won) {
            System.out.print("Your guess: ");
            int guess = scanner.nextInt();
            attempts++;

            if (guess < secretNumber) {
                System.out.println("Too low! Try again.");
            } else if (guess > secretNumber) {
                System.out.println("Too high! Try again.");
            } else {
                won = true;
                System.out.println("\n🎉 Correct! You got it in " + attempts + " attempts!");
            }
        }

        scanner.close();
    }
}
```

### Example: Simple Text Adventure

```java
import java.util.Scanner;

public class TextAdventure {

    static Scanner scanner = new Scanner(System.in);
    static int health = 100;
    static int gold = 0;

    public static void main(String[] args) {
        System.out.println("=== THE DUNGEON ===");
        System.out.println("You wake up in a dark dungeon...\n");
        roomOne();
    }

    static void roomOne() {
        System.out.println("You see two doors: [1] Left  [2] Right");
        System.out.print("Choose: ");
        int choice = scanner.nextInt();

        if (choice == 1) {
            System.out.println("You find a chest with 50 gold!");
            gold += 50;
            roomTwo();
        } else {
            System.out.println("A monster attacks! You lose 30 HP.");
            health -= 30;
            System.out.println("HP: " + health + " | Gold: " + gold);
            roomTwo();
        }
    }

    static void roomTwo() {
        if (health <= 0) {
            System.out.println("\n💀 Game Over! You died.");
            return;
        }
        System.out.println("\nYou reach the exit!");
        System.out.println("Final stats — HP: " + health + " | Gold: " + gold);
        System.out.println("🏆 You escaped the dungeon!");
    }
}
```

### Key techniques for terminal games

```java
// Clear screen (works on most terminals)
System.out.print("\033[H\033[2J");
System.out.flush();

// Colored text (ANSI codes)
System.out.println("\033[31mRed text\033[0m");   // red
System.out.println("\033[32mGreen text\033[0m"); // green
System.out.println("\033[33mYellow text\033[0m");// yellow
System.out.println("\033[0mReset color\033[0m"); // reset

// Add a delay (pause between turns)
try {
    Thread.sleep(1000);  // pause 1 second
} catch (InterruptedException e) {
    Thread.currentThread().interrupt();
}

// Read a single character choice
Scanner sc = new Scanner(System.in);
String input = sc.nextLine().trim().toLowerCase();
```

### Game loop pattern
```java
boolean running = true;

while (running) {
    displayStatus();       // show HP, score, inventory
    String action = getInput();  // read player input

    switch (action) {
        case "n" -> moveNorth();
        case "s" -> moveSouth();
        case "attack" -> attackEnemy();
        case "quit" -> running = false;
        default -> System.out.println("Unknown command.");
    }

    checkWinLose();        // did the player win or die?
}
```

---

## 24. Making UI with Java (Swing)

Java's built-in **Swing** library lets you build desktop GUIs — windows, buttons, text fields, menus, and more. No extra installation needed.

### Your first window

```java
import javax.swing.*;

public class FirstWindow {
    public static void main(String[] args) {
        // Always create UI on the Event Dispatch Thread
        SwingUtilities.invokeLater(() -> {
            JFrame frame = new JFrame("My First Window");
            frame.setSize(400, 300);
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setLocationRelativeTo(null);  // center on screen
            frame.setVisible(true);
        });
    }
}
```

### Adding components

```java
import javax.swing.*;
import java.awt.*;

public class SimpleForm {
    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            JFrame frame = new JFrame("Simple Form");
            frame.setSize(350, 200);
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setLayout(new FlowLayout());  // simple layout

            JLabel label   = new JLabel("Enter your name:");
            JTextField field  = new JTextField(15);
            JButton button = new JButton("Greet");
            JLabel result  = new JLabel("");

            // Button click action
            button.addActionListener(e -> {
                String name = field.getText();
                result.setText("Hello, " + name + "!");
            });

            frame.add(label);
            frame.add(field);
            frame.add(button);
            frame.add(result);
            frame.setLocationRelativeTo(null);
            frame.setVisible(true);
        });
    }
}
```

### Common Swing components

```java
JLabel label        = new JLabel("Text label");
JButton button      = new JButton("Click me");
JTextField field    = new JTextField(20);          // single-line input
JTextArea area      = new JTextArea(5, 20);        // multi-line input
JCheckBox check     = new JCheckBox("Accept terms");
JRadioButton radio  = new JRadioButton("Option A");
JComboBox<String> combo = new JComboBox<>(new String[]{"A", "B", "C"});
JSlider slider      = new JSlider(0, 100, 50);     // min, max, initial
JPasswordField pass = new JPasswordField(15);
JSpinner spinner    = new JSpinner();

// Scrollable text area
JScrollPane scroll = new JScrollPane(area);

// Message dialogs
JOptionPane.showMessageDialog(frame, "Done!");
int choice = JOptionPane.showConfirmDialog(frame, "Are you sure?");
String input = JOptionPane.showInputDialog("Enter value:");
```

### Layouts

```java
// FlowLayout — components flow left to right
frame.setLayout(new FlowLayout());

// BorderLayout — North/South/East/West/Center
frame.setLayout(new BorderLayout());
frame.add(new JButton("Top"),    BorderLayout.NORTH);
frame.add(new JButton("Bottom"), BorderLayout.SOUTH);
frame.add(new JButton("Center"), BorderLayout.CENTER);

// GridLayout — rows x columns grid
frame.setLayout(new GridLayout(3, 2));  // 3 rows, 2 columns

// GridBagLayout — flexible, complex layouts
// BoxLayout — horizontal or vertical stacking
JPanel panel = new JPanel();
panel.setLayout(new BoxLayout(panel, BoxLayout.Y_AXIS));  // vertical
```

### Custom drawing with JPanel

```java
import javax.swing.*;
import java.awt.*;

public class DrawingExample extends JPanel {

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        Graphics2D g2 = (Graphics2D) g;

        // Anti-aliasing for smooth lines
        g2.setRenderingHint(RenderingHints.KEY_ANTIALIASING,
                            RenderingHints.VALUE_ANTIALIAS_ON);

        // Draw shapes
        g2.setColor(Color.BLUE);
        g2.fillRect(50, 50, 100, 60);      // filled rectangle

        g2.setColor(Color.RED);
        g2.drawOval(200, 50, 80, 80);      // circle outline

        g2.setColor(Color.GREEN);
        g2.fillOval(320, 50, 80, 80);      // filled circle

        // Draw text
        g2.setColor(Color.BLACK);
        g2.setFont(new Font("Arial", Font.BOLD, 20));
        g2.drawString("Hello, Graphics!", 50, 180);

        // Draw a line
        g2.setColor(Color.ORANGE);
        g2.setStroke(new BasicStroke(3));
        g2.drawLine(50, 220, 400, 220);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            JFrame frame = new JFrame("Drawing");
            frame.add(new DrawingExample());
            frame.setSize(500, 300);
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setLocationRelativeTo(null);
            frame.setVisible(true);
        });
    }
}
```

### Key events and mouse events

```java
// Key listener
frame.addKeyListener(new KeyAdapter() {
    @Override
    public void keyPressed(KeyEvent e) {
        if (e.getKeyCode() == KeyEvent.VK_SPACE) {
            System.out.println("Space pressed!");
        }
        if (e.getKeyCode() == KeyEvent.VK_LEFT) {
            System.out.println("Left arrow!");
        }
    }
});
frame.setFocusable(true);

// Mouse listener on a panel
panel.addMouseListener(new MouseAdapter() {
    @Override
    public void mouseClicked(MouseEvent e) {
        System.out.println("Clicked at: " + e.getX() + ", " + e.getY());
    }
});
```

---

## 25. Making Animations with Java

Animations in Java are created by repeatedly updating state and repainting the screen — typically 30 to 60 times per second using a **Swing Timer** or a **game loop thread**.

### Basic animation with Swing Timer

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class BouncingBall extends JPanel implements ActionListener {

    int x = 100, y = 100;       // ball position
    int dx = 3, dy = 2;         // speed (pixels per frame)
    final int RADIUS = 25;
    Timer timer;

    public BouncingBall() {
        setBackground(Color.BLACK);
        timer = new Timer(16, this);  // ~60 FPS (16ms per frame)
        timer.start();
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        // Move the ball
        x += dx;
        y += dy;

        // Bounce off walls
        if (x - RADIUS < 0 || x + RADIUS > getWidth())  dx = -dx;
        if (y - RADIUS < 0 || y + RADIUS > getHeight()) dy = -dy;

        repaint();  // trigger paintComponent
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);  // clear screen
        Graphics2D g2 = (Graphics2D) g;
        g2.setRenderingHint(RenderingHints.KEY_ANTIALIASING,
                            RenderingHints.VALUE_ANTIALIAS_ON);
        g2.setColor(Color.CYAN);
        g2.fillOval(x - RADIUS, y - RADIUS, RADIUS * 2, RADIUS * 2);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            JFrame frame = new JFrame("Bouncing Ball");
            frame.add(new BouncingBall());
            frame.setSize(600, 400);
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setLocationRelativeTo(null);
            frame.setVisible(true);
        });
    }
}
```

### Moving a sprite with keyboard controls

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class MovingPlayer extends JPanel {

    int playerX = 200, playerY = 200;
    final int SPEED = 5;
    final int SIZE = 30;

    public MovingPlayer() {
        setBackground(Color.DARK_GRAY);
        setFocusable(true);

        addKeyListener(new KeyAdapter() {
            @Override
            public void keyPressed(KeyEvent e) {
                switch (e.getKeyCode()) {
                    case KeyEvent.VK_UP    -> playerY -= SPEED;
                    case KeyEvent.VK_DOWN  -> playerY += SPEED;
                    case KeyEvent.VK_LEFT  -> playerX -= SPEED;
                    case KeyEvent.VK_RIGHT -> playerX += SPEED;
                }
                // Clamp to screen
                playerX = Math.max(0, Math.min(getWidth() - SIZE, playerX));
                playerY = Math.max(0, Math.min(getHeight() - SIZE, playerY));
                repaint();
            }
        });
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        g.setColor(Color.YELLOW);
        g.fillRect(playerX, playerY, SIZE, SIZE);

        g.setColor(Color.WHITE);
        g.drawString("Use arrow keys to move!", 10, 20);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            JFrame frame = new JFrame("Move the Square");
            frame.add(new MovingPlayer());
            frame.setSize(600, 400);
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setLocationRelativeTo(null);
            frame.setVisible(true);
        });
    }
}
```

### Smooth game loop using a thread

```java
public class GameLoop extends JPanel implements Runnable {

    private Thread gameThread;
    private boolean running = true;
    private double angle = 0;  // rotating shape angle

    public GameLoop() {
        setBackground(Color.BLACK);
        gameThread = new Thread(this);
        gameThread.start();
    }

    @Override
    public void run() {
        // Fixed timestep: target 60 FPS
        long targetTime = 1000 / 60;

        while (running) {
            long start = System.currentTimeMillis();

            update();   // game logic
            repaint();  // draw

            long elapsed = System.currentTimeMillis() - start;
            long sleepTime = targetTime - elapsed;
            if (sleepTime > 0) {
                try { Thread.sleep(sleepTime); }
                catch (InterruptedException e) { Thread.currentThread().interrupt(); }
            }
        }
    }

    void update() {
        angle += 2;  // rotate 2 degrees per frame
        if (angle >= 360) angle = 0;
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        Graphics2D g2 = (Graphics2D) g;

        int cx = getWidth() / 2;
        int cy = getHeight() / 2;

        g2.setColor(Color.GREEN);
        g2.translate(cx, cy);
        g2.rotate(Math.toRadians(angle));
        g2.fillRect(-40, -40, 80, 80);  // spinning square
        g2.rotate(-Math.toRadians(angle));
        g2.translate(-cx, -cy);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            JFrame frame = new JFrame("Game Loop");
            frame.add(new GameLoop());
            frame.setSize(500, 400);
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setLocationRelativeTo(null);
            frame.setVisible(true);
        });
    }
}
```

### Animation tips

| Goal | Technique |
|------|-----------|
| Simple timed animation | `javax.swing.Timer` (16ms = ~60 FPS) |
| Game loop with fixed timestep | Dedicated `Thread` with `Thread.sleep()` |
| Smooth movement | Update position by small increments each frame |
| Flicker-free rendering | Always call `super.paintComponent(g)` first |
| Rotating/scaling shapes | Use `Graphics2D.rotate()` and `Graphics2D.scale()` |
| Load an image | `ImageIcon icon = new ImageIcon("player.png")` |
| Draw an image | `g.drawImage(icon.getImage(), x, y, null)` |

---

## 26. Best Practices & Common Mistakes

### ✅ Good habits

```java
// 1. NEVER use == to compare Strings
String a = "hello";
String b = new String("hello");
a == b;           // might be false! (different objects)
a.equals(b);      // true — always use .equals()

// 2. Check for null before using
if (name != null && !name.isEmpty()) {
    System.out.println(name.toUpperCase());
}

// Or use Optional to force null handling
Optional.ofNullable(name)
    .ifPresent(n -> System.out.println(n.toUpperCase()));

// 3. Use StringBuilder for string concatenation in loops
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i);  // much faster than: result += i
}

// 4. Close resources with try-with-resources
try (InputStream is = new FileInputStream("file.txt")) {
    // use is
}  // auto-closed

// 5. Use enhanced for loop when possible
for (String item : list) { }  // not: for (int i = 0; i < list.size(); i++)

// 6. Prefer List over ArrayList in type declarations
List<String> list = new ArrayList<>();  // flexible — can change implementation
// not: ArrayList<String> list = new ArrayList<>();

// 7. Always @Override when overriding
@Override
public String toString() { return "..."; }

// 8. Use final for constants
private static final int MAX_SIZE = 100;

// 9. Fail fast — validate early
public void setAge(int age) {
    if (age < 0) throw new IllegalArgumentException("Age cannot be negative");
    this.age = age;
}
```

### ❌ Common mistakes

```java
// 1. NullPointerException
String s = null;
s.length();   // CRASH
// Fix: check null, or use Optional

// 2. == for String comparison
"hello" == "hello"  // might be false
// Fix: use .equals()

// 3. Infinite loop with float
float f = 0.0f;
while (f != 1.0f) {  // may never equal 1.0 due to floating point!
    f += 0.1f;
}
// Fix: use counter or check with epsilon

// 4. Modifying list while iterating
for (String s : list) {
    list.remove(s);   // ConcurrentModificationException!
}
// Fix: use Iterator.remove() or collect to remove list
list.removeIf(s -> s.startsWith("A"));  // Java 8+

// 5. Integer overflow
int max = Integer.MAX_VALUE;
int overflow = max + 1;   // becomes MIN_VALUE — silent overflow!
// Fix: use long for large numbers

// 6. Not handling exceptions
void readFile(String path) {
    // if this throws IOException, program crashes
    BufferedReader br = new BufferedReader(new FileReader(path));
}
// Fix: wrap in try-catch or declare throws

// 7. Mutable objects as Map keys
Map<List<Integer>, String> map = new HashMap<>();
List<Integer> key = new ArrayList<>(List.of(1, 2, 3));
map.put(key, "value");
key.add(4);  // mutate the key!
map.get(key);  // null — hash changed, can't find it
// Fix: use immutable keys (String, Integer, record, etc.)

// 8. Thread-unsafe code
// Multiple threads accessing same variable without synchronization
private int count = 0;
public void increment() { count++; }  // NOT thread-safe
// Fix: use synchronized, AtomicInteger, or locks
```

---

## 27. Quick Reference Cheat Sheet

### Primitive types

| Type | Size | Range |
|------|------|-------|
| `byte` | 1 byte | -128 to 127 |
| `short` | 2 bytes | -32,768 to 32,767 |
| `int` | 4 bytes | ±2.1 billion |
| `long` | 8 bytes | ±9.2 × 10^18 |
| `float` | 4 bytes | 7 decimal digits |
| `double` | 8 bytes | 15 decimal digits |
| `char` | 2 bytes | single Unicode char |
| `boolean` | 1 byte | true / false |

### Which collection to use?

| Situation | Use |
|-----------|-----|
| Ordered list, fast index access | `ArrayList` |
| Fast add/remove at front and back | `LinkedList` |
| Key-value pairs, fast lookup | `HashMap` |
| Key-value pairs, sorted | `TreeMap` |
| Unique elements, fast lookup | `HashSet` |
| Unique elements, sorted | `TreeSet` |
| FIFO queue | `LinkedList` as `Queue` |
| LIFO stack | `ArrayDeque` |
| Priority processing | `PriorityQueue` |

### String methods
```java
s.length()             // length
s.charAt(i)            // character at index
s.substring(a, b)      // substring from a to b (exclusive)
s.indexOf(sub)         // position (-1 if not found)
s.contains(sub)        // boolean
s.startsWith(pre)      // boolean
s.endsWith(suf)        // boolean
s.replace(old, new)    // replace all
s.toUpperCase()        // uppercase
s.toLowerCase()        // lowercase
s.trim()               // remove leading/trailing spaces
s.strip()              // same but handles unicode spaces
s.split(regex)         // split to String[]
s.isEmpty()            // length == 0
s.isBlank()            // empty or only whitespace
String.valueOf(x)      // convert anything to String
s.equals(t)            // equality (not ==!)
s.equalsIgnoreCase(t)  // case-insensitive equals
```

### Math class
```java
Math.abs(x)         // absolute value
Math.sqrt(x)        // square root
Math.pow(x, y)      // x^y
Math.max(a, b)      // maximum
Math.min(a, b)      // minimum
Math.floor(x)       // round down
Math.ceil(x)        // round up
Math.round(x)       // round to nearest
Math.random()       // random double 0.0 to 1.0
Math.PI             // 3.14159...
Math.E              // 2.71828...
```

### Common imports
```java
import java.util.*;            // ArrayList, HashMap, Scanner, etc.
import java.util.stream.*;     // Streams
import java.util.function.*;   // Function, Predicate, Consumer, etc.
import java.util.Optional;     // Optional
import java.io.*;              // File I/O
import java.nio.file.*;        // Modern file I/O
import java.util.concurrent.*; // Threads, ExecutorService
```

---

*Java rewards patience. Start with section 1, build small projects, and sections 22–25 (Minecraft plugins, terminal games, UI, and animations) will be totally within reach before you know it.*
