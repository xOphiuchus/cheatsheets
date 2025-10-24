# C++ Cheatsheet

## Basics

**What it is:** The foundational elements of any C++ program.  
**Why it's important:** Every C++ program builds upon these fundamental concepts.

**Basic syntax and usage:**

```cpp
#include <iostream> // A library for input/output

int main() { // Main function, program execution starts here
    std::cout << "Hello, World!"; // Outputting text
    return 0; // Indicates successful execution
}
```

**Key things to remember:** Programs start in `main()`, use `#include` for libraries, and `return 0` usually means success.

**Example Use Case:** A simple "Hello, World!" program.

---

## Comments

**What it is:** Non-executable lines of code used for explanation.  
**Why it's important:** Makes code understandable for humans, aids debugging.

**Basic syntax and usage:**

```cpp
// Single-line comment
/*
Multi-line
comment
*/
```

**Key things to remember:** Use generously to clarify complex logic.

**Example Use Case:** Explaining a tricky algorithm step-by-step.

---

## Libraries

**What it is:** Collections of pre-written code (functions, classes) that provide specific functionalities.  
**Why it's important:** Reusability, saves time, provides optimized solutions.

**Basic syntax and usage:**

```cpp
#include <iostream> // Includes the iostream library
#include <vector>   // Includes the vector library
```

**Key things to remember:** Use `#include` to bring them into your program. Angle brackets (`<>`) for standard libraries, quotes (`""`) for your own header files.

**Example Use Case:** Using `<cmath>` for mathematical functions like `sqrt()`.

---

## Namespace std

**What it is:** A logical grouping for standard C++ library components to avoid naming conflicts.  
**Why it's important:** Prevents clashes between names in different libraries or your own code.

**Basic syntax and usage:**

```cpp
std::cout << "Hello"; // Explicitly using std namespace
using namespace std; // Brings all names from std into current scope
cout << "Hello";     // Now you can use cout directly
```

**Key things to remember:** `using namespace std;` is convenient but can lead to naming collisions in large projects. Prefer `std::` prefix for clarity or `using std::cout;` for specific items.

**Example Use Case:** Almost all standard C++ code uses std for cout, cin, vector, etc.

---

## Cout / Endl

**What it is:** `cout` is used for outputting data to the console, `endl` for inserting a newline and flushing the output buffer.  
**Why it's important:** Primary way to display information to the user or for debugging.

**Basic syntax and usage:**

```cpp
std::cout << "My name is " << "John" << std::endl;
```

**Key things to remember:** `<<` is the insertion operator. `endl` flushes the buffer, which can be slower than `'\n'` if flushing isn't immediately needed.

**Example Use Case:** Printing the result of a calculation.

---

## Main

**What it is:** The entry point of every C++ program. Execution begins here.  
**Why it's important:** It's where your program starts running.

**Basic syntax and usage:**

```cpp
int main() {
    // Your code here
    return 0;
}
```

**Key things to remember:** Must return an int. 0 typically indicates successful execution.

**Example Use Case:** Any executable C++ program will have a main function.

---

## Variables

**What it is:** Named storage locations in memory to hold data.  
**Why it's important:** Allows programs to store and manipulate data dynamically.

**Basic syntax and usage:**

```cpp
int age = 30;         // Integer variable
double price = 19.99; // Double-precision floating-point variable
char initial = 'J';   // Character variable
```

**Key things to remember:** Declare variables before using them, choose appropriate data types.

**Example Use Case:** Storing a user's age, a product price, or a name.

---

## Global Variables

**What it is:** Variables declared outside any function, accessible from anywhere in the program.  
**Why it's important:** Provides universal access to certain data, but often discouraged due to potential side effects.

**Basic syntax and usage:**

```cpp
int globalVar = 100; // Global variable

int main() {
    // Can access globalVar here
    return 0;
}
```

**Key things to remember:** Can lead to hard-to-track bugs. Prefer passing data as function arguments or using classes when possible.

**Example Use Case:** Rarely recommended, but sometimes used for truly global constants or shared resources that are read-only.

---

## Constants

**What it is:** Variables whose values cannot be changed after initialization.  
**Why it's important:** Ensures data integrity, makes code more readable, and can enable compiler optimizations.

**Basic syntax and usage:**

```cpp
const double PI = 3.14159;
const int MAX_USERS = 100;
```

**Key things to remember:** Use `const` keyword. Good practice for fixed values.

**Example Use Case:** Storing mathematical constants like PI, or fixed configuration values.

---

## Data Types

**What it is:** Classifies the type of value a variable can hold (e.g., integer, floating-point, character).  
**Why it's important:** Determines how memory is allocated and what operations can be performed.

**Basic syntax and usage:**

```cpp
int num = 10;
float temp = 98.6f;
bool isTrue = true;
std::string name = "Alice";
```

**Key things to remember:** Choose the smallest data type that can hold the required range of values.

**Example Use Case:** int for counting, double for precise measurements, char for single letters.

---

## Float Precision

**What it is:** The accuracy and range of floating-point numbers (`float` and `double`). `double` offers more precision than `float`.  
**Why it's important:** Critical for calculations where accuracy matters (e.g., financial, scientific).

**Basic syntax and usage:**

```cpp
float singlePrecision = 1.234567f;   // Typically 7 decimal digits precision
double doublePrecision = 1.23456789012345; // Typically 15-17 decimal digits precision
```

**Key things to remember:** `double` is generally preferred for most floating-point operations unless memory is extremely constrained.

**Example Use Case:** Calculating very precise measurements in engineering.

---

## Printf

**What it is:** A function from the C standard library for formatted output.  
**Why it's important:** Provides powerful formatting capabilities for displaying data.

**Basic syntax and usage:**

```cpp
#include <cstdio> // For printf
int age = 30;
printf("My age is %d and my name is %s.\n", age, "Bob");
```

**Key things to remember:** Uses format specifiers (e.g., `%d` for int, `%s` for string, `%f` for float/double). Requires `<cstdio>`.

**Example Use Case:** Printing a report with aligned columns of data.

---

## Auto

**What it is:** A keyword that allows the compiler to deduce the data type of a variable from its initializer.  
**Why it's important:** Reduces verbosity, especially with complex types, and helps prevent type mismatches.

**Basic syntax and usage:**

```cpp
auto num = 10;           // num is int
auto pi = 3.14159;       // pi is double
auto name = "Charlie";   // name is const char*
std::vector<int> numbers = {1, 2, 3};
for (auto it = numbers.begin(); it != numbers.end(); ++it) {
    // it's type is std::vector<int>::iterator
}
```

**Key things to remember:** Must be initialized at declaration. Not for dynamically changing types.

**Example Use Case:** Iterating through containers with complex iterator types.

---

## Cin

**What it is:** Used to read input from the console (keyboard).  
**Why it's important:** Allows programs to interact with the user and receive data.

**Basic syntax and usage:**

```cpp
#include <iostream>
int num;
std::cout << "Enter a number: ";
std::cin >> num;
std::cout << "You entered: " << num << std::endl;
```

**Key things to remember:** `>>` is the extraction operator. Handles basic data types. Be aware of input errors.

**Example Use Case:** Getting user input for a calculator program.

---

## Casting

**What it is:** Converting a value from one data type to another.  
**Why it's important:** Necessary when operations require specific types, or to prevent data loss.

**Basic syntax and usage:**

```cpp
double d = 3.14;
int i = static_cast<int>(d); // C++ style cast, preferred
int j = (int)d;             // C-style cast, less safe
```

**Key things to remember:** `static_cast` for safe conversions between related types. `dynamic_cast` for polymorphic types, `const_cast` for removing constness, `reinterpret_cast` for low-level reinterpretation.

**Example Use Case:** Converting a float to an int to get the whole number part.

---

## Math Operators

**What it is:** Symbols used to perform mathematical calculations.  
**Why it's important:** Fundamental for any numerical computation.

**Basic syntax and usage:**

```cpp
int a = 10, b = 3;
int sum = a + b;     // Addition: 13
int diff = a - b;    // Subtraction: 7
int product = a * b; // Multiplication: 30
int quotient = a / b; // Division: 3 (integer division)
int remainder = a % b; // Modulo: 1
```

**Key things to remember:** Integer division truncates. Modulo works only with integers. Operator precedence applies.

**Example Use Case:** Calculating the total cost of items.

---

## Conditional / Logical Operators

**What it is:** Operators used to compare values and combine conditions.  
**Why it's important:** Enables decision-making and control flow in programs.

**Basic syntax and usage:**

```cpp
// Conditional (Comparison) Operators:
// == (equal to), != (not equal to), < (less than), > (greater than),
// <= (less than or equal to), >= (greater than or equal to)
int x = 5, y = 10;
bool isEqual = (x == y); // false
bool isGreater = (y > x); // true

// Logical Operators:
// && (AND), || (OR), ! (NOT)
bool condition1 = true;
bool condition2 = false;
bool resultAnd = condition1 && condition2; // false
bool resultOr = condition1 || condition2;  // true
bool resultNot = !condition1;              // false
```

**Key things to remember:** Return true or false. Used heavily in if, while, and for statements.

**Example Use Case:** Checking if a user's age is within a valid range AND if they have agreed to terms.

---

## If / Else If / Else

**What it is:** Control structures for executing different blocks of code based on conditions.  
**Why it's important:** Allows programs to make decisions and respond to different inputs or states.

**Basic syntax and usage:**

```cpp
int score = 85;
if (score >= 90) {
    std::cout << "Grade A" << std::endl;
} else if (score >= 80) {
    std::cout << "Grade B" << std::endl;
} else {
    std::cout << "Grade C or lower" << std::endl;
}
```

**Key things to remember:** Only one block will execute. Conditions are evaluated in order.

**Example Use Case:** Determining a student's grade based on their score.

---

## Ternary Operator

**What it is:** A shorthand for a simple if-else statement, often used for assigning a value conditionally.  
**Why it's important:** Makes code more compact for simple conditional assignments.

**Basic syntax and usage:**

```cpp
int age = 18;
std::string status = (age >= 18) ? "Adult" : "Minor";
std::cout << status << std::endl;
```

**Key things to remember:** `condition ? value_if_true : value_if_false;`

**Example Use Case:** Assigning a default value if a variable is null or empty.

---

## Arrays

**What it is:** A fixed-size collection of elements of the same data type, stored in contiguous memory locations.  
**Why it's important:** Efficient for storing and accessing a fixed number of similar items.

**Basic syntax and usage:**

```cpp
int numbers[5];        // Declares an array of 5 integers
numbers[0] = 10;       // Assigns value to the first element (index 0)
int scores[] = {80, 90, 75}; // Initializes with values (size is inferred)
std::cout << scores[1] << std::endl; // Accessing element at index 1 (90)
```

**Key things to remember:** Fixed size. Zero-indexed. No built-in bounds checking (can lead to errors).

**Example Use Case:** Storing the days of the week, or a list of temperatures for a week.

---

## Vectors

**What it is:** A dynamic array from the Standard Template Library (STL) that can grow or shrink in size.  
**Why it's important:** Provides the flexibility of dynamic sizing with efficient access like arrays.

**Basic syntax and usage:**

```cpp
#include <vector>
std::vector<int> nums;         // Empty vector
nums.push_back(10);            // Add element to end
nums.push_back(20);
std::cout << nums[0] << std::endl; // Access element
std::cout << nums.size() << std::endl; // Get size
```

**Key things to remember:** Part of STL. Dynamically resizes. Provides methods like push_back, pop_back, size(), empty().

**Example Use Case:** Storing a list of unknown number of user inputs, or managing a collection of game objects that can be added/removed.

---
