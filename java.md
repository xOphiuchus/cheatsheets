# Java Programming Cheatsheet

---

## 1. Introduction to Java ☕

- **What:** High-level, object-oriented, platform-independent language.
- **Why:** Widely used for enterprise, Android, and cross-platform apps.
- **Syntax:**
  ```java
  public class HelloWorld {
      public static void main(String[] args) {
          System.out.println("Hello, Java!");
      }
  }
  ```
- **Key:** Entry point is `main`. Case-sensitive, semicolons end statements.
- **Example:** Console app to print a message.

---

## 2. Variables ❎

- **What:** Containers for data, must declare type.
- **Why:** Store and manipulate data.
- **Syntax:**
  ```java
  int speed = 100;
  double price = 19.99;
  String name = "Alex";
  ```
- **Key:** Statically typed, must initialize before use.
- **Example:** Store user age, price, or name.

---

## 3. User Input ⌨️

- **What:** Read data from user.
- **Why:** Interactive programs.
- **Syntax:**
  ```java
  import java.util.Scanner;
  Scanner sc = new Scanner(System.in);
  String name = sc.nextLine();
  int age = sc.nextInt();
  sc.close();
  ```
- **Key:** Use correct Scanner method for type.
- **Example:** Prompt for login or calculation input.

---

## 4. Arithmetic 🧮

- **What:** Math operations: +, -, \*, /, %.
- **Why:** Calculations and logic.
- **Syntax:**
  ```java
  int sum = a + b;
  double result = (double)a / b;
  ```
- **Key:** Integer division truncates; cast for decimals.
- **Example:** Calculate totals, averages.

---

## 5. If Statements 🤔

- **What:** Conditional execution.
- **Why:** Control flow.
- **Syntax:**
  ```java
  if (score >= 70) { ... } else { ... }
  ```
- **Key:** Condition must be boolean.
- **Example:** Check login, shipping cost.

---

## 6. Random & Math 📐

- **What:** Generate random numbers, math functions.
- **Why:** Games, calculations.
- **Syntax:**
  ```java
  int dice = (int)(Math.random() * 6) + 1;
  double sq = Math.sqrt(16);
  ```
- **Key:** Math methods are static.
- **Example:** Dice roll, hypotenuse.

---

## 7. printf 🖨️

- **What:** Formatted output.
- **Why:** Control display, align numbers.
- **Syntax:**
  ```java
  System.out.printf("PI: %.2f\n", 3.14);
  ```
- **Key:** Use format specifiers (%d, %s, %.2f).
- **Example:** Financial reports.

---

## 8. String Methods & Substrings 🧵

- **What:** Manipulate and extract text.
- **Why:** Parsing, validation.
- **Syntax:**
  ```java
  String s = "Hello";
  int len = s.length();
  String part = s.substring(1, 4);
  ```
- **Key:** Strings are immutable, index starts at 0.
- **Example:** Validate phone, extract code.

---

## 9. Ternary Operator ❔

- **What:** Shorthand if-else for assignment.
- **Why:** Concise conditional logic.
- **Syntax:**
  ```java
  String status = (age >= 18) ? "Adult" : "Minor";
  ```
- **Key:** Use for simple assignments.
- **Example:** Set discount rate.

---

## 10. Switch (Enhanced) 💡

- **What:** Multi-way branch, modern arrow syntax.
- **Why:** Cleaner than chained if-else.
- **Syntax:**
  ```java
  String type = switch(day) {
      case "MON" -> "Weekday";
      case "SAT", "SUN" -> "Weekend";
      default -> "Invalid";
  };
  ```
- **Key:** No break needed with arrow syntax.
- **Example:** Day type, product category.

---

## 11. Logical Operators ❕

- **What:** Combine boolean expressions: &&, ||, !.
- **Why:** Complex conditions.
- **Syntax:**
  ```java
  if (a > 0 && b < 10) { ... }
  ```
- **Key:** Short-circuit evaluation.
- **Example:** Access control.

---

## 12. Loops (while, for, for-each) 🔂

- **What:** Repeat code blocks.
- **Why:** Process collections, repeat tasks.
- **Syntax:**
  ```java
  while (cond) { ... }
  for (int i = 0; i < n; i++) { ... }
  for (String s : arr) { ... }
  ```
- **Key:** For known or unknown iterations.
- **Example:** Input validation, process list.

---

## 13. Break & Continue 🚦

- **What:** Control loop flow.
- **Why:** Exit or skip iterations.
- **Syntax:**
  ```java
  if (x == 3) continue;
  if (x == 7) break;
  ```
- **Key:** Use sparingly for clarity.
- **Example:** Stop search, skip archived.

---

## 14. Methods 📞

- **What:** Named code blocks, can take parameters and return values.
- **Why:** Reuse and organize code.
- **Syntax:**
  ```java
  public static int add(int a, int b) { return a + b; }
  ```
- **Key:** Static for class-level, otherwise instance.
- **Example:** Calculate tax.

---

## 15. Arrays 🍎

- **What:** Fixed-size, ordered collection.
- **Why:** Store related data.
- **Syntax:**
  ```java
  int[] nums = new int[5];
  nums[0] = 10;
  ```
- **Key:** Zero-indexed, fixed size.
- **Example:** Daily temperatures.

---

## 16. ArrayLists 📃

- **What:** Resizable array (List).
- **Why:** Flexible collections.
- **Syntax:**
  ```java
  ArrayList<String> list = new ArrayList<>();
  list.add("A");
  String first = list.get(0);
  ```
- **Key:** Only objects, not primitives.
- **Example:** Shopping cart.

---

## 17. HashMaps 🗺️

- **What:** Key-value pairs, fast lookup.
- **Why:** Dictionaries, settings.
- **Syntax:**
  ```java
  HashMap<String, Integer> map = new HashMap<>();
  map.put("A", 1);
  int v = map.get("A");
  ```
- **Key:** Keys unique, values can repeat.
- **Example:** User preferences.

---

## 18. Classes & Objects 🧱

- **What:** Blueprints (classes), instances (objects).
- **Why:** OOP, model real-world entities.
- **Syntax:**
  ```java
  class Car { String color; void drive() { ... } }
  Car c = new Car();
  ```
- **Key:** Fields and methods, use `new` to create.
- **Example:** Bank account, car.

---

## 19. Constructors 🔨

- **What:** Special method to initialize objects.
- **Why:** Set initial state.
- **Syntax:**
  ```java
  public Car(String color) { this.color = color; }
  ```
- **Key:** Same name as class, no return type.
- **Example:** Set radius for Circle.

---

## 20. Static 🤝

- **What:** Belongs to class, not instance.
- **Why:** Shared data/methods.
- **Syntax:**
  ```java
  static int count = 0;
  static void inc() { count++; }
  ```
- **Key:** Access via class name.
- **Example:** Math.PI, object counter.

---

## 21. Inheritance 👨‍👧‍👦

- **What:** Child class extends parent.
- **Why:** Code reuse, hierarchy.
- **Syntax:**
  ```java
  class Dog extends Animal { ... }
  ```
- **Key:** Single inheritance, use `super` for parent.
- **Example:** Car extends Vehicle.

---

## 22. Method Overriding ♻️

- **What:** Child redefines parent method.
- **Why:** Specialized behavior.
- **Syntax:**
  ```java
  @Override
  public void draw() { ... }
  ```
- **Key:** Same signature, use `@Override`.
- **Example:** Dog's makeSound().

---

## 23. Interfaces 📋

- **What:** Contract of methods to implement.
- **Why:** Multiple inheritance, abstraction.
- **Syntax:**
  ```java
  interface Drivable { void start(); }
  class Car implements Drivable { ... }
  ```
- **Key:** Can implement multiple interfaces.
- **Example:** Flyable, Drivable.

---

## 24. Polymorphism 🎭

- **What:** Many forms; parent reference, child object.
- **Why:** Generic, flexible code.
- **Syntax:**
  ```java
  Animal a = new Dog();
  a.speak(); // Calls Dog's speak
  ```
- **Key:** Actual object type determines method at runtime.
- **Example:** List of Shape, call draw().

---

## 25. Getters & Setters 🔐

- **What:** Public methods to access private fields.
- **Why:** Encapsulation, validation.
- **Syntax:**
  ```java
  private int age;
  public int getAge() { return age; }
  public void setAge(int a) { age = a; }
  ```
- **Key:** Fields private, methods public.
- **Example:** setTemperature() with validation.

---

## 26. Exception Handling ⚠️

- **What:** Handle runtime errors.
- **Why:** Robust, safe code.
- **Syntax:**
  ```java
  try { ... } catch (Exception e) { ... } finally { ... }
  ```
- **Key:** Use try-catch for risky code.
- **Example:** File IO, user input.

---

## 27. File IO ✍️📖

- **What:** Read/write files.
- **Why:** Persist data.
- **Syntax:**
  ```java
  FileWriter w = new FileWriter("f.txt");
  w.write("hi"); w.close();
  Scanner r = new Scanner(new File("f.txt"));
  while (r.hasNextLine()) { System.out.println(r.nextLine()); }
  r.close();
  ```
- **Key:** Always close files, handle exceptions.
- **Example:** Save/load settings.

---

## 28. Enums 📅

- **What:** Fixed set of constants.
- **Why:** Type-safe, readable code.
- **Syntax:**
  ```java
  enum Day { MON, TUE, WED }
  Day d = Day.MON;
  ```
- **Key:** Use in switch, comparisons.
- **Example:** Traffic light states.

---

## 29. Threading 🧵

- **What:** Run code concurrently.
- **Why:** Responsive, efficient apps.
- **Syntax:**
  ```java
  class MyTask implements Runnable { public void run() { ... } }
  new Thread(new MyTask()).start();
  ```
- **Key:** Use start(), not run().
- **Example:** Web server, background tasks.

---
