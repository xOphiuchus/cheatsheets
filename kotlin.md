# Kotlin Cheatsheet

Last Updated : 10 Oct, 2025

---

## 1. Hello World

What it is: Simple program that verifies environment setup.

Why it's important: Confirms compilation and execution flow.

Basic syntax and usage:

```kotlin
fun main() {
    println("Hello, World!")
}
```

Key things to remember: `fun main()` is the entry point; no class wrapper required.

Example use case: Quick sanity check for a new project.

---

## 2. val and var

What it is: Variable declarations. `val` — immutable, `var` — mutable.

Why it's important: Encourages immutability and safer code.

Basic syntax and usage:

```kotlin
val name = "Alice" // cannot be reassigned
var age = 30       // can be updated
age += 1
```

Key things to remember: Prefer `val` unless reassignment is required.

Example use case: Use `val` for config constants — `val maxRetries = 3`.

---

## 3. Arithmetic Operators

What it is: +, -, \*, /, % operations.

Why it's important: Core for calculations.

Basic syntax and usage:

```kotlin
val sum = 5 + 3
val div = 5 / 2     // integer division when both are Int
val ddiv = 5.0 / 2  // float division
val mod = 5 % 3     // remainder
```

Key things to remember: Type matters for division.

Example use case: Computing totals and tax.

---

## 4. Comparison Operators

What it is: Compare values returning Boolean.

Why it's important: Controls program flow and conditions.

Basic syntax and usage:

```kotlin
val isEqual = (a == b)
val notEqual = (a != b)
val gt = (a > b)
```

Key things to remember: `==` checks structural equality; `===` checks referential equality.

Example use case: Password matching and validation.

---

## 5. Logical Operators

What it is: Combine boolean expressions: &&, ||, !.

Why it's important: Build complex conditions.

Basic syntax and usage:

```kotlin
val ok = isLoggedIn && isAdmin
val proceed = flag || override
val not = !done
```

Key things to remember: Kotlin uses short-circuit evaluation.

Example use case: Conditional access checks.

---

## 6. Console Input

What it is: Read user input from the terminal.

Why it's important: Makes CLI programs interactive.

Basic syntax and usage:

```kotlin
print("Enter name: ")
val name = readLine() ?: "Guest"
println("Hello, $name")
```

Key things to remember: `readLine()` returns `String?` and needs null handling.

Example use case: Small interactive utilities or scripts.

---

## 7. Nullability & Null-Safe Operators

What it is: Kotlin's null-safety; types are non-null by default.

Why it's important: Prevents many runtime NullPointerExceptions.

Basic syntax and usage:

```kotlin
var s: String? = null
val len = s?.length           // safe-call
val size = s?.length ?: 0     // Elvis operator
// val fail = s!!.length      // throws if s is null
```

Key things to remember: Prefer `?.` and `?:` over `!!`.

Example use case: Handling optional fields in JSON parsing.

---

## 8. if / else

What it is: Conditional branching. `if` is an expression.

Why it's important: Decision-making and conditional assignments.

Basic syntax and usage:

```kotlin
val grade = if (score >= 90) "A" else "B"
if (x > 0) println("positive")
```

Key things to remember: `if` can return values.

Example use case: Assigning status based on thresholds.

---

## 9. when (switch-like)

What it is: Replacement for switch; more expressive.

Why it's important: Cleaner branching for many conditions.

Basic syntax and usage:

```kotlin
when (x) {
  0 -> println("Zero")
  in 1..9 -> println("One to Nine")
  else -> println("Other")
}
```

Key things to remember: `when` is exhaustive as an expression if you return values.

Example use case: Handling API status codes or UI states.

---

## 10. Exceptions / try / catch / finally

What it is: Error handling mechanism.

Why it's important: Handles runtime errors gracefully.

Basic syntax and usage:

```kotlin
val number = try {
  "123a".toInt()
} catch (e: NumberFormatException) {
  0
} finally {
  println("Attempted conversion")
}
```

Key things to remember: `try` is an expression and can return values.

Example use case: Safely parse user input.

---

## 11. Arrays

What it is: Fixed-size collection of elements.

Why it's important: Efficient low-level storage.

Basic syntax and usage:

```kotlin
val arr = arrayOf("a", "b", "c")
val intArr = intArrayOf(1, 2, 3)
println(arr[0])
```

Key things to remember: Use `Array<T>` or specialized arrays for primitives.

Example use case: Lookup tables, small fixed lists.

---

## 12. Loops

What it is: `for`, `while`, looping constructs.

Why it's important: Iterate over collections and ranges.

Basic syntax and usage:

```kotlin
for (i in 0..5) println(i)     // inclusive
for (x in list) println(x)
while (x < 10) { x++ }
```

Key things to remember: Use `until` for exclusive end: `0 until n`.

Example use case: Iterate list of results to print or transform.

---

## 13. Functions

What it is: Reusable named blocks of code.

Why it's important: Organize logic and reuse.

Basic syntax and usage:

```kotlin
fun add(a: Int, b: Int): Int = a + b
fun greet(name: String) { println("Hi, $name") }
```

Key things to remember: Use expression functions for brevity.

Example use case: Utility helpers like `formatDate()`.

---

## 14. Extension Functions

What it is: Add new functions to existing classes without inheritance.

Why it's important: Improve readability and avoid utility classes.

Basic syntax and usage:

```kotlin
fun String.shout() = this.toUpperCase()
println("hello".shout()) // HELLO
```

Key things to remember: Cannot access private members on the extended type.

Example use case: `String.nextChar()` or `List<T>.second()` helpers.

---

## 15. Function Overloading

What it is: Multiple functions with same name but different signatures.

Why it's important: Provide API convenience.

Basic syntax and usage:

```kotlin
fun print(x: Int) { println(x) }
fun print(x: String) { println(x) }
```

Key things to remember: Overloading is based on parameter types and counts.

Example use case: `toJson(obj: Any)` and `toJson(list: List<Any>)`.

---

## 16. Lambda Expressions

What it is: Anonymous functions, used everywhere in Kotlin stdlib.

Why it's important: Enables functional programming idioms.

Basic syntax and usage:

```kotlin
val doubler: (Int) -> Int = { it * 2 }
val list = listOf(1,2,3).map { it * 2 }
```

Key things to remember: Use `it` for single-parameter lambdas.

Example use case: Transform a list with `.map`, filter with `.filter`.

---

## 17. Classes and Data Classes

What it is: `class` for behavior and `data class` for value containers.

Why it's important: Encapsulate logic and model data succinctly.

Basic syntax and usage:

```kotlin
class Person(val name: String) {
  fun greet() = println("Hello, $name")
}

data class Point(val x: Int, val y: Int)
val p = Point(1,2)
```

Key things to remember: `data class` auto-generates `toString`, `equals`, and `copy`.

Example use case: Use `data class` for DTOs.

---

## 18. Interfaces

What it is: Contracts that classes implement.

Why it's important: Enables polymorphism and modularity.

Basic syntax and usage:

```kotlin
interface Clickable {
  fun click()
  fun doubleClick() { println("Default") } // default impl
}
class Button: Clickable {
  override fun click() = println("Clicked")
}
```

Key things to remember: Interfaces can have default implementations.

Example use case: UI interfaces or event handlers.

---

## 19. Abstract Classes

What it is: Base classes that cannot be instantiated.

Why it's important: Provide shared behavior and enforce method contracts.

Basic syntax and usage:

```kotlin
abstract class Animal {
  abstract fun speak()
  fun eat() = println("eating")
}
class Dog : Animal() {
  override fun speak() = println("Woof")
}
```

Key things to remember: Can hold both abstract and concrete members.

Example use case: Base classes for service layers.

---

## 20. Sealed Classes / Sealed Interfaces

What it is: Closed hierarchies enabling exhaustive `when` checks.

Why it's important: Useful for state modeling and safe branching.

Basic syntax and usage:

```kotlin
sealed class Result
data class Success(val data: String): Result()
object Error: Result()

fun handle(r: Result) = when(r) {
  is Success -> println(r.data)
  is Error -> println("error")
}
```

Key things to remember: Subclasses must be in the same file; `when` can be exhaustive.

Example use case: Representing API response states (Loading / Success / Error).

---

## 21. Enum Classes

What it is: Predefined set of constants.

Why it's important: Make state choices type-safe.

Basic syntax and usage:

```kotlin
enum class Direction { NORTH, EAST, SOUTH, WEST }
val d = Direction.NORTH
```

Key things to remember: Enums can have properties and functions.

Example use case: Representing user roles or app modes.

---

## 22. Object Singletons

What it is: `object` creates a single instance.

Why it's important: Simple global state or utilities.

Basic syntax and usage:

```kotlin
object Logger {
  fun log(msg: String) = println("LOG: $msg")
}
Logger.log("Start")
```

Key things to remember: `object` is lazy-initialized and thread-safe.

Example use case: an application-wide configuration or cache.

---

## 23. Visibility Modifiers

What it is: Control access: `public`, `private`, `protected`, `internal`.

Why it's important: Encapsulation and API control.

Basic syntax and usage:

```kotlin
internal class Repo { private fun encrypt() {} }
```

Key things to remember: `internal` limits to module; `protected` only in subclasses.

Example use case: Mark helper methods `private` within a class.

---

## 24. Generics

What it is: Type parameters for reusable, type-safe containers/functions.

Why it's important: Avoid casting and improve type safety.

Basic syntax and usage:

```kotlin
class Box<T>(val value: T)
fun <T> single(item: T): List<T> = listOf(item)
```

Key things to remember: Use `in`/`out` for variance when needed.

Example use case: `Repository<T>` for persisting different entity types.

---

## 25. Coroutines (Basic intro)

What it is: Lightweight concurrency primitives in Kotlin.

Why it's important: Makes asynchronous code concise and sequential-looking.

Basic syntax and usage:

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
  launch { delay(100); println("World") }
  println("Hello")
}
```

Key things to remember: `suspend` functions and `Dispatchers` for context.

Example use case: Concurrent I/O operations in an Android or server app.

---

## 26. Collections (List/Set/Map examples)

What it is: Core collection types.

Why it's important: Used for storing and organizing many elements.

Basic syntax and usage:

```kotlin
val list: List<Int> = listOf(1, 2)
val mutable: MutableList<Int> = mutableListOf(1)
val set = setOf("a", "b")
val map = mapOf("x" to 10, "y" to 20)
```

Key things to remember: Prefer immutable interfaces when possible.

Example use case: Caching and grouping items for processing.

---
