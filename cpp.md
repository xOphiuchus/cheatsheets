# C++ Cheatsheet

## Basics

What it is: The foundational elements of any C++ program.

Why it's important: Every C++ program builds upon these fundamental concepts.

Basic syntax and usage: Understanding the structure of a C++ program.

C++

```cpp
#include <iostream> // A library for input/output

int main() { // Main function, program execution starts here
    std::cout << "Hello, World!"; // Outputting text
    return 0; // Indicates successful execution
}
```

Key things to remember: Programs start in main(), use #include for libraries, and return 0 usually means success.

Example Use Case: A simple "Hello, World!" program.

---

## Comments

What it is: Non-executable lines of code used for explanation.

Why it's important: Makes code understandable for humans, aids debugging.

Basic syntax and usage:

C++

```cpp
// Single-line comment
/*
Multi-line
comment
*/
```

Key things to remember: Use generously to clarify complex logic.

Example Use Case: Explaining a tricky algorithm step-by-step.

---

## Libraries

What it is: Collections of pre-written code (functions, classes) that provide specific functionalities.

Why it's important: Reusability, saves time, provides optimized solutions.

Basic syntax and usage:

C++

```cpp
#include <iostream> // Includes the iostream library
#include <vector>   // Includes the vector library
```

Key things to remember: Use #include to bring them into your program. Angle brackets (<>) for standard libraries, quotes ("") for your own header files.

Example Use Case: Using <cmath> for mathematical functions like sqrt().

---

## Namespace std

What it is: A logical grouping for standard C++ library components to avoid naming conflicts.

Why it's important: Prevents clashes between names in different libraries or your own code.

Basic syntax and usage:

C++

```cpp
std::cout << "Hello"; // Explicitly using std namespace
using namespace std; // Brings all names from std into current scope
cout << "Hello";     // Now you can use cout directly
```

Key things to remember: using namespace std; is convenient but can lead to naming collisions in large projects. Prefer std:: prefix for clarity or using std::cout; for specific items.

Example Use Case: Almost all standard C++ code uses std for cout, cin, vector, etc.

---

## Cout / Endl

What it is: cout is used for outputting data to the console, endl for inserting a newline and flushing the output buffer.

Why it's important: Primary way to display information to the user or for debugging.

Basic syntax and usage:

C++

```cpp
std::cout << "My name is " << "John" << std::endl;
```

Key things to remember: << is the insertion operator. endl flushes the buffer, which can be slower than '\n' if flushing isn't immediately needed.

Example Use Case: Printing the result of a calculation.

---

## Main

What it is: The entry point of every C++ program. Execution begins here.

Why it's important: It's where your program starts running.

Basic syntax and usage:

C++

```cpp
int main() {
    // Your code here
    return 0;
}
```

Key things to remember: Must return an int. 0 typically indicates successful execution.

Example Use Case: Any executable C++ program will have a main function.

---

## Variables

What it is: Named storage locations in memory to hold data.

Why it's important: Allows programs to store and manipulate data dynamically.

Basic syntax and usage:

C++

```cpp
int age = 30;         // Integer variable
double price = 19.99; // Double-precision floating-point variable
char initial = 'J';   // Character variable
```

Key things to remember: Declare variables before using them, choose appropriate data types.

Example Use Case: Storing a user's age, a product price, or a name.

---

## Global Variables

What it is: Variables declared outside any function, accessible from anywhere in the program.

Why it's important: Provides universal access to certain data, but often discouraged due to potential side effects.

Basic syntax and usage:

C++

```cpp
int globalVar = 100; // Global variable

int main() {
    // Can access globalVar here
    return 0;
}
```

Key things to remember: Can lead to hard-to-track bugs. Prefer passing data as function arguments or using classes when possible.

Example Use Case: Rarely recommended, but sometimes used for truly global constants or shared resources that are read-only.

---

## Constants

What it is: Variables whose values cannot be changed after initialization.

Why it's important: Ensures data integrity, makes code more readable, and can enable compiler optimizations.

Basic syntax and usage:

C++

```cpp
const double PI = 3.14159;
const int MAX_USERS = 100;
```

Key things to remember: Use const keyword. Good practice for fixed values.

Example Use Case: Storing mathematical constants like PI, or fixed configuration values.

---

## Data Types

What it is: Classifies the type of value a variable can hold (e.g., integer, floating-point, character).

Why it's important: Determines how memory is allocated and what operations can be performed.

Basic syntax and usage:

C++

```cpp
int num = 10;
float temp = 98.6f;
bool isTrue = true;
std::string name = "Alice";
```

Key things to remember: Choose the smallest data type that can hold the required range of values.

Example Use Case: int for counting, double for precise measurements, char for single letters.

---

## Float Precision

What it is: The accuracy and range of floating-point numbers (float and double). double offers more precision than float.

Why it's important: Critical for calculations where accuracy matters (e.g., financial, scientific).

Basic syntax and usage:

C++

```cpp
float singlePrecision = 1.234567f;   // Typically 7 decimal digits precision
double doublePrecision = 1.23456789012345; // Typically 15-17 decimal digits precision
```

Key things to remember: double is generally preferred for most floating-point operations unless memory is extremely constrained.

Example Use Case: Calculating very precise measurements in engineering.

---

## Printf

What it is: A function from the C standard library for formatted output.

Why it's important: Provides powerful formatting capabilities for displaying data.

Basic syntax and usage:

C++

```cpp
#include <cstdio> // For printf
// or <iostream> in some compilers will allow it.
int age = 30;
printf("My age is %d and my name is %s.\n", age, "Bob");
```

Key things to remember: Uses format specifiers (e.g., %d for int, %s for string, %f for float/double). Requires <cstdio>.

Example Use Case: Printing a report with aligned columns of data.

---

## Auto

What it is: A keyword that allows the compiler to deduce the data type of a variable from its initializer.

Why it's important: Reduces verbosity, especially with complex types, and helps prevent type mismatches.

Basic syntax and usage:

C++

```cpp
auto num = 10;           // num is int
auto pi = 3.14159;       // pi is double
auto name = "Charlie";   // name is const char*
std::vector<int> numbers = {1, 2, 3};
for (auto it = numbers.begin(); it != numbers.end(); ++it) {
    // it's type is std::vector<int>::iterator
}
```

Key things to remember: Must be initialized at declaration. Not for dynamically changing types.

Example Use Case: Iterating through containers with complex iterator types.

---

## Cin

What it is: Used to read input from the console (keyboard).

Why it's important: Allows programs to interact with the user and receive data.

Basic syntax and usage:

C++

```cpp
#include <iostream>
int num;
std::cout << "Enter a number: ";
std::cin >> num;
std::cout << "You entered: " << num << std::endl;
```

Key things to remember: >> is the extraction operator. Handles basic data types. Be aware of input errors.

Example Use Case: Getting user input for a calculator program.

---

## Casting

What it is: Converting a value from one data type to another.

Why it's important: Necessary when operations require specific types, or to prevent data loss.

Basic syntax and usage:

C++

```cpp
double d = 3.14;
int i = static_cast<int>(d); // C++ style cast, preferred
int j = (int)d;             // C-style cast, less safe
```

Key things to remember: static_cast for safe conversions between related types. dynamic_cast for polymorphic types, const_cast for removing constness, reinterpret_cast for low-level reinterpretation.

Example Use Case: Converting a float to an int to get the whole number part.

---

## Math Operators

What it is: Symbols used to perform mathematical calculations.

Why it's important: Fundamental for any numerical computation.

Basic syntax and usage:

C++

```cpp
int a = 10, b = 3;
int sum = a + b;     // Addition: 13
int diff = a - b;    // Subtraction: 7
int product = a * b; // Multiplication: 30
int quotient = a / b; // Division: 3 (integer division)
int remainder = a % b; // Modulo: 1
```

Key things to remember: Integer division truncates. Modulo works only with integers. Operator precedence applies.

Example Use Case: Calculating the total cost of items.

---

## Conditional / Logical Operators

What it is: Operators used to compare values and combine conditions.

Why it's important: Enables decision-making and control flow in programs.

Basic syntax and usage:

C++

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

Key things to remember: Return true or false. Used heavily in if, while, and for statements.

Example Use Case: Checking if a user's age is within a valid range AND if they have agreed to terms.

---

## If / Else If / Else

What it is: Control structures for executing different blocks of code based on conditions.

Why it's important: Allows programs to make decisions and respond to different inputs or states.

Basic syntax and usage:

C++

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

Key things to remember: Only one block will execute. Conditions are evaluated in order.

Example Use Case: Determining a student's grade based on their score.

---

## Ternary Operator

What it is: A shorthand for a simple if-else statement, often used for assigning a value conditionally.

Why it's important: Makes code more compact for simple conditional assignments.

Basic syntax and usage:

C++

```cpp
int age = 18;
std::string status = (age >= 18) ? "Adult" : "Minor";
// Equivalent to:
// std::string status;
// if (age >= 18) {
//     status = "Adult";
// } else {
//     status = "Minor";
// }
std::cout << status << std::endl;
```

Key things to remember: condition ? value_if_true : value_if_false;

Example Use Case: Assigning a default value if a variable is null or empty.

---

## Arrays

What it is: A fixed-size collection of elements of the same data type, stored in contiguous memory locations.

Why it's important: Efficient for storing and accessing a fixed number of similar items.

Basic syntax and usage:

C++

```cpp
int numbers[5];        // Declares an array of 5 integers
numbers[0] = 10;       // Assigns value to the first element (index 0)
int scores[] = {80, 90, 75}; // Initializes with values (size is inferred)
std::cout << scores[1] << std::endl; // Accessing element at index 1 (90)
```

Key things to remember: Fixed size. Zero-indexed. No built-in bounds checking (can lead to errors).

Example Use Case: Storing the days of the week, or a list of temperatures for a week.

---

## Vectors

What it is: A dynamic array from the Standard Template Library (STL) that can grow or shrink in size.

Why it's important: Provides the flexibility of dynamic sizing with efficient access like arrays.

Basic syntax and usage:

C++

```cpp
#include <vector>
std::vector<int> nums;         // Empty vector
nums.push_back(10);            // Add element to end
nums.push_back(20);
std::cout << nums[0] << std::endl; // Access element
std::cout << nums.size() << std::endl; // Get size
```

Key things to remember: Part of STL. Dynamically resizes. Provides methods like push_back, pop_back, size(), empty().

Example Use Case: Storing a list of unknown number of user inputs, or managing a collection of game objects that can be added/removed.

---

## While Loop

What it is: A control flow statement that allows code to be executed repeatedly based on a given condition.

Why it's important: Enables repeated execution of a block of code as long as the condition is true.

Basic syntax and usage:

C++

```cpp
int count = 0;
while (count < 5) {
    std::cout << count << std::endl;
    count++;
}
```

Key things to remember: The condition is evaluated before each iteration. If the condition is false initially, the loop body will not execute.

Example Use Case: Repeatedly asking for user input until a valid response is given.

---

## Break/Continue

What it is: `break` exits the nearest enclosing loop or switch statement. `continue` skips the rest of the current loop iteration and proceeds with the next iteration.

Why it's important: Provides finer control over loop execution.

Basic syntax and usage:

C++

```cpp
for (int i = 0; i < 10; i++) {
    if (i == 5) break; // Exits the loop when i is 5
    if (i % 2 == 0) continue; // Skips the rest of the loop body for even i
    std::cout << i << std::endl;
}
```

Key things to remember: `break` can be used to exit a loop early, and `continue` can be used to skip to the next iteration.

Example Use Case: Searching for an item in a list and exiting the loop once it's found.

---

## String Stream

What it is: A string stream is an input/output stream that operates on strings. It allows reading from and writing to strings as if they were streams.

Why it's important: Useful for parsing and formatting strings, and for converting between strings and other data types.

Basic syntax and usage:

C++

```cpp
#include <sstream>
std::stringstream ss;
ss << "The answer is " << 42;
std::string str = ss.str(); // Converts the stream to a string
```

Key things to remember: `std::stringstream` is used for string streams. Use `.str()` to retrieve the string from the stream.

Example Use Case: Building a complex string from multiple variables and values.

---

## Getline

What it is: A function to read a line of text from an input stream into a string.

Why it's important: Allows reading of entire lines, including spaces, until a newline character is found.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <string>

std::string line;
std::cout << "Enter a line of text: ";
std::getline(std::cin, line);
std::cout << "You entered: " << line << std::endl;
```

Key things to remember: `std::getline` can read lines with spaces, unlike `std::cin >>`. Be cautious of newline characters in input.

Example Use Case: Reading a full address or sentence from user input.

---

## For Loop

What it is: A control flow statement for specifying iteration, allowing code to be executed repeatedly for a fixed number of times.

Why it's important: Provides a concise way to iterate over ranges, collections, or to repeat actions.

Basic syntax and usage:

C++

```cpp
for (int i = 0; i < 5; i++) {
    std::cout << i << std::endl;
}

// Range-based for loop (C++11 and later)
std::vector<int> vec = {1, 2, 3, 4, 5};
for (int num : vec) {
    std::cout << num << std::endl;
}
```

Key things to remember: The loop variable is scoped to the for statement. In the range-based for loop, the collection type determines the loop variable type.

Example Use Case: Iterating over an array or vector to process each element.

---

## Random

What it is: Facilities to generate random numbers.

Why it's important: Enables the creation of random data, which is essential in simulations, games, and testing.

Basic syntax and usage:

C++

```cpp
#include <cstdlib> // For rand() and srand()
#include <ctime>   // For time()

std::srand(std::time(0)); // Seed the random number generator
int randomNumber = std::rand(); // Generate a random number
```

Key things to remember: `std::rand()` generates a pseudo-random number. Use `std::srand()` to seed the generator, typically with the current time.

Example Use Case: Generating a random password or token.

---

## Do While

What it is: A control flow statement that executes a block of code once, and then repeats the execution as long as a given condition is true.

Why it's important: Ensures that the code block is executed at least once, regardless of the condition.

Basic syntax and usage:

C++

```cpp
int count = 0;
do {
    std::cout << count << std::endl;
    count++;
} while (count < 5);
```

Key things to remember: The condition is evaluated after the execution of the loop body. Guarantees at least one execution of the loop body.

Example Use Case: Displaying a menu to the user at least once before checking if they want to exit.

---

## Strings

What it is: Strings are sequences of characters used to represent text.

Why it's important: Essential for handling and manipulating text data.

Basic syntax and usage:

C++

```cpp
#include <string>

std::string greeting = "Hello, World!";
std::string name;
std::cout << "Enter your name: ";
std::getline(std::cin, name);
std::cout << greeting << " " << name << std::endl;
```

Key things to remember: Strings are objects of the `std::string` class. Use `std::getline` to read strings with spaces.

Example Use Case: Storing and manipulating user input, such as names or messages.

---

## Character Functions

What it is: Functions that operate on individual characters or strings, such as checking character properties or converting case.

Why it's important: Useful for parsing and validating text data.

Basic syntax and usage:

C++

```cpp
#include <cctype> // For character functions

char ch = 'a';
if (std::isalpha(ch)) {
    std::cout << ch << " is a letter." << std::endl;
}

std::string text = "Hello";
for (char& c : text) {
    c = std::toupper(c); // Convert each character to uppercase
}
```

Key things to remember: Character functions are in the `<cctype>` header. They can be used to inspect and manipulate individual characters.

Example Use Case: Validating and formatting user input, such as ensuring a password contains both letters and numbers.

---

## Math Functions

What it is: Predefined functions for performing mathematical operations, such as trigonometry, logarithms, and exponentiation.

Why it's important: Provides a wide range of mathematical computations without the need to implement algorithms manually.

Basic syntax and usage:

C++

```cpp
#include <cmath> // For math functions

double result = std::sqrt(16.0); // Square root
double power = std::pow(2.0, 3.0); // Power
double logarithm = std::log(100.0); // Natural logarithm
```

Key things to remember: Math functions are in the `<cmath>` header. They operate on and return floating-point numbers.

Example Use Case: Performing scientific calculations, such as computing the trajectory of a projectile.

---

## Functions

What it is: Blocks of code that perform a specific task, defined by the programmer, and can be reused throughout the code.

Why it's important: Promotes code reusability, modularity, and easier debugging.

Basic syntax and usage:

C++

```cpp
#include <iostream>

// Function declaration
void greet(std::string name);

// Main function
int main() {
    greet("Alice");
    return 0;
}

// Function definition
void greet(std::string name) {
    std::cout << "Hello, " << name << "!" << std::endl;
}
```

Key things to remember: Functions can have parameters and return values. They must be declared before they are used.

Example Use Case: Any reusable piece of code, such as a function to calculate the area of a rectangle.

---

## Pointers

What it is: Variables that store the memory address of another variable.

Why it's important: Allows direct memory management and manipulation, which can lead to more efficient code.

Basic syntax and usage:

C++

```cpp
#include <iostream>

int main() {
    int var = 42;
    int* ptr = &var; // Pointer to var

    std::cout << "Value of var: " << var << std::endl;
    std::cout << "Address of var: " << &var << std::endl;
    std::cout << "Value of ptr: " << ptr << std::endl;
    std::cout << "Value pointed to by ptr: " << *ptr << std::endl;

    return 0;
}
```

Key things to remember: Pointers are declared with an asterisk (_) before the variable name. Use the address-of operator (&) to get a variable's address, and the dereference operator (_) to access the value at that address.

Example Use Case: Dynamic memory allocation, arrays, and function arguments passing by reference.

---

## Exception Handling

What it is: A mechanism to handle runtime errors, allowing the normal flow of the program to be maintained.

Why it's important: Prevents program crashes and allows for graceful error recovery.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <stdexcept> // For std::exception

int main() {
    try {
        throw std::runtime_error("An error occurred");
    } catch (const std::exception& e) {
        std::cout << "Exception caught: " << e.what() << std::endl;
    }

    return 0;
}
```

Key things to remember: Use `try` to define a block of code to be tested for errors, and `catch` to define a block of code to handle the error. The `throw` keyword is used to raise an exception.

Example Use Case: Handling file I/O errors, network errors, or any other runtime anomalies.

---

## Classes/Objects

What it is: A class is a blueprint for creating objects (a particular data structure), providing initial values for state (member variables) and implementations of behavior (member functions or methods).

Why it's important: Fundamental for object-oriented programming, allowing for encapsulation, inheritance, and polymorphism.

Basic syntax and usage:

C++

```cpp
#include <iostream>

// Class definition
class Dog {
public:
    // Constructor
    Dog(std::string n) : name(n) {}

    // Method
    void bark() {
        std::cout << name << " says woof!" << std::endl;
    }

private:
    std::string name;
};

// Main function
int main() {
    Dog dog("Buddy"); // Create an object of Dog
    dog.bark(); // Call the bark method

    return 0;
}
```

Key things to remember: Classes are defined with the `class` keyword. Members are accessed with the dot operator (.). Use `public`, `private`, and `protected` access specifiers to control access to class members.

Example Use Case: Modeling real-world entities, such as cars, animals, or buildings.

---

## Header File

What it is: A file containing C++ declarations and macro definitions to be shared between several source files.

Why it's important: Promotes code reusability and modularity. Allows separation of interface and implementation.

Basic syntax and usage:

C++ Header File (`example.h`)

```cpp
#ifndef EXAMPLE_H
#define EXAMPLE_H

void hello();

#endif
```

C++ Source File (`example.cpp`)

```cpp
#include "example.h"
#include <iostream>

void hello() {
    std::cout << "Hello, World!" << std::endl;
}
```

Main File

```cpp
#include "example.h"

int main() {
    hello();
    return 0;
}
```

Key things to remember: Header files have a `.h` extension and are included in source files with `#include`. Use include guards (`#ifndef`, `#define`, `#endif`) to prevent multiple inclusions.

Example Use Case: Declaring functions, classes, and variables to be shared across multiple source files.

---

## Private/Protected/Public

What it is: Access specifiers in a class that control the visibility and accessibility of class members.

Why it's important: Encapsulates the class data and methods, restricting access to the internal implementation.

Basic syntax and usage:

C++

```cpp
class MyClass {
public:
    int publicVar; // Accessible from outside the class

protected:
    int protectedVar; // Accessible in derived classes

private:
    int privateVar; // Accessible only within this class
};
```

Key things to remember: `public` members are accessible from outside the class, `protected` members are accessible in derived classes, and `private` members are accessible only within the class.

Example Use Case: Hiding the internal state and requiring all interaction to occur through member functions.

---

## Static

What it is: A keyword that can be used to define static variables and functions, which have a global lifetime but local visibility.

Why it's important: Static variables maintain their value between function calls, and static functions cannot be called from outside the file they are declared in.

Basic syntax and usage:

C++

```cpp
#include <iostream>

void function() {
    static int count = 0; // Static variable
    count++;
    std::cout << count << std::endl;
}

int main() {
    function();
    function();
    function();

    return 0;
}
```

Key things to remember: Static variables are initialized only once and retain their value between calls. Static functions are not visible outside the translation unit.

Example Use Case: Counting the number of times a function is called, or restricting the visibility of a function to the file it is declared in.

---

## Constructor

What it is: A special member function of a class that is executed whenever an object of that class is created.

Why it's important: Used to initialize objects, allocate resources, and perform setup operations.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class MyClass {
public:
    // Constructor
    MyClass() {
        std::cout << "Constructor called!" << std::endl;
    }
};

int main() {
    MyClass obj; // Constructor is called here

    return 0;
}
```

Key things to remember: Constructors have the same name as the class and do not have a return type. They can be overloaded.

Example Use Case: Initializing member variables, allocating dynamic memory, or opening files.

---

## Overloading Functions

What it is: Defining multiple functions with the same name but different parameters (type or number) in the same scope.

Why it's important: Provides flexibility to call the same function name with different arguments.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class Print {
public:
    void message(int i) {
        std::cout << "Integer: " << i << std::endl;
    }

    void message(double d) {
        std::cout << "Double: " << d << std::endl;
    }

    void message(int i, double d) {
        std::cout << "Integer: " << i << ", Double: " << d << std::endl;
    }
};

int main() {
    Print obj;
    obj.message(5);
    obj.message(3.14);
    obj.message(10, 2.718);

    return 0;
}
```

Key things to remember: Function overloading is resolved at compile time. The correct function is chosen based on the arguments used in the call.

Example Use Case: Providing multiple ways to call a function, such as different units of measurement.

---

## Deconstructor

What it is: A special member function of a class that is executed when an object of that class is destroyed.

Why it's important: Used to release resources, deallocate memory, and perform cleanup operations.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class MyClass {
public:
    // Destructor
    ~MyClass() {
        std::cout << "Destructor called!" << std::endl;
    }
};

int main() {
    MyClass obj; // Constructor is called
    // Destructor will be called automatically when obj goes out of scope

    return 0;
}
```

Key things to remember: Destructors have the same name as the class, preceded by a tilde (~). They cannot be overloaded, and a class can have only one destructor.

Example Use Case: Releasing resources, such as closing files or freeing memory allocated with `new`.

---

## Setters/Getters

What it is: Setter and getter methods are used to set and get the values of private member variables of a class.

Why it's important: Provides controlled access to the class members, allowing validation and encapsulation.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class MyClass {
private:
    int value;

public:
    // Setter
    void setValue(int v) {
        value = v;
    }

    // Getter
    int getValue() {
        return value;
    }
};

int main() {
    MyClass obj;
    obj.setValue(42);
    std::cout << "Value: " << obj.getValue() << std::endl;

    return 0;
}
```

Key things to remember: Setters and getters are public member functions. Setters usually return void, and getters usually return the member variable's type.

Example Use Case: Validating and setting a value, such as ensuring a temperature is within a valid range.

---

## Static Methods

What it is: Methods that belong to the class rather than any object instance and can be called on the class itself.

Why it's important: Allows operations that are related to the class but do not require access to instance data.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class MyClass {
public:
    static void staticMethod() {
        std::cout << "Static method called!" << std::endl;
    }
};

int main() {
    MyClass::staticMethod(); // Call static method

    return 0;
}
```

Key things to remember: Static methods are declared with the `static` keyword. They cannot access non-static members or methods.

Example Use Case: Factory methods that create instances of the class, or utility functions related to the class.

---

## Virtual

What it is: A keyword used to declare a virtual function, which can be overridden in derived classes to provide polymorphic behavior.

Why it's important: Enables dynamic dispatch, allowing the program to decide at runtime which function to call.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class Base {
public:
    virtual void show() {
        std::cout << "Base class show function called." << std::endl;
    }
};

class Derived : public Base {
public:
    void show() override { // Override the base class function
        std::cout << "Derived class show function called." << std::endl;
    }
};

int main() {
    Base* b;           // Base class pointer
    Derived d;        // Derived class object
    b = &d;

    b->show();        // Calls Derived's show() due to virtual function

    return 0;
}
```

Key things to remember: Virtual functions are declared with the `virtual` keyword in the base class. Use `override` in the derived class to indicate that a function is overriding a base class virtual function.

Example Use Case: Implementing polymorphism, where a base class reference or pointer is used to refer to derived class objects.

---

## Implementation File

What it is: A source file (`.cpp` file) where the class methods and functions are defined and implemented.

Why it's important: Separates the interface (header file) from the implementation, promoting modularity and reducing compilation dependencies.

Basic syntax and usage:

C++ Header File (`example.h`)

```cpp
#ifndef EXAMPLE_H
#define EXAMPLE_H

void hello();

#endif
```

C++ Implementation File (`example.cpp`)

```cpp
#include "example.h"
#include <iostream>

void hello() {
    std::cout << "Hello, World!" << std::endl;
}
```

Main File

```cpp
#include "example.h"

int main() {
    hello();
    return 0;
}
```

Key things to remember: The implementation file includes the header file where the functions are declared. The header file guards (`#ifndef`, `#define`, `#endif`) prevent multiple inclusions.

Example Use Case: Defining the behavior of functions and methods declared in header files.

---

## This

What it is: A pointer available in non-static member functions of a class, pointing to the object for which the member function is called.

Why it's important: Allows access to the object's members and methods, and is essential for implementing certain patterns like the copy-and-swap idiom.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class MyClass {
public:
    void show() {
        std::cout << "Value: " << this->value << std::endl;
    }

    MyClass& setValue(int value) {
        this->value = value;
        return *this;
    }

private:
    int value;
};

int main() {
    MyClass obj;
    obj.setValue(42).show(); // Chaining calls

    return 0;
}
```

Key things to remember: `this` is an implicit pointer passed to all non-static member functions. It cannot be modified or reseated.

Example Use Case: Returning `*this` from a setter method to allow method chaining.

---

## Pointer Operator

What it is: The `->` operator is used to access members of a class or structure through a pointer.

Why it's important: Provides a way to access object members when you have a pointer to the object.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class MyClass {
public:
    void show() {
        std::cout << "Hello, World!" << std::endl;
    }
};

int main() {
    MyClass obj;
    MyClass* ptr = &obj; // Pointer to obj

    ptr->show(); // Calls obj's show() using pointer

    return 0;
}
```

Key things to remember: The pointer operator (`->`) is used with pointers to objects, while the dot operator (`.`) is used with object instances.

Example Use Case: Accessing members of an object that is being referenced or pointed to.

---

## Polymorphism

What it is: The ability of different classes to be treated as instances of the same class through common interfaces, typically achieved via inheritance and virtual functions.

Why it's important: Enables one interface to be used for a general class of actions, making code more flexible and extensible.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class Base {
public:
    virtual void show() {
        std::cout << "Base class show function called." << std::endl;
    }
};

class Derived : public Base {
public:
    void show() override { // Override the base class function
        std::cout << "Derived class show function called." << std::endl;
    }
};

void display(Base& obj) {
    obj.show(); // Calls the appropriate show() function
}

int main() {
    Base b;
    Derived d;

    display(b); // Calls Base's show()
    display(d); // Calls Derived's show()

    return 0;
}
```

Key things to remember: Polymorphism is achieved through virtual functions and inheritance. The correct function is determined at runtime based on the object type.

Example Use Case: Designing flexible and reusable code, such as a graphics program that can draw different shapes (circles, squares) using the same interface.

---

## Inheritance

What it is: A mechanism where a new class (derived class) inherits the properties and behaviors (members) of an existing class (base class).

Why it's important: Promotes code reusability and establishes a natural hierarchy between classes.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class Base {
public:
    void show() {
        std::cout << "Base class show function called." << std::endl;
    }
};

class Derived : public Base {
public:
    void display() {
        std::cout << "Derived class display function called." << std::endl;
    }
};

int main() {
    Derived obj;
    obj.show();    // Calls Base's show()
    obj.display(); // Calls Derived's display()

    return 0;
}
```

Key things to remember: Inheritance is specified in the class definition (e.g., `class Derived : public Base`). The derived class inherits all accessible members of the base class.

Example Use Case: Creating a class hierarchy for a zoo application with base class `Animal` and derived classes `Lion`, `Tiger`, etc.

---

## Call Super Functions

What it is: Calling a base class's function from a derived class, typically used to extend or modify the base class behavior.

Why it's important: Allows derived classes to build upon or customize the behavior of base classes.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class Base {
public:
    void show() {
        std::cout << "Base class show function called." << std::endl;
    }
};

class Derived : public Base {
public:
    void show() {
        Base::show(); // Call Base's show()
        std::cout << "Derived class show function called." << std::endl;
    }
};

int main() {
    Derived obj;
    obj.show(); // Calls Derived's show(), which calls Base's show()

    return 0;
}
```

Key things to remember: Use the scope resolution operator (`::`) to call a base class function. This is often used in constructors, destructors, and overridden methods.

Example Use Case: Extending the initialization of a base class in a derived class constructor.

---

## Creating Objects

What it is: The process of allocating memory for and initializing a new instance of a class.

Why it's important: Objects are the building blocks of C++ programs, representing real-world entities or concepts.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class MyClass {
public:
    void show() {
        std::cout << "Hello, World!" << std::endl;
    }
};

int main() {
    MyClass obj; // Stack allocation
    obj.show();

    MyClass* ptr = new MyClass(); // Heap allocation
    ptr->show();
    delete ptr; // Free allocated memory

    return 0;
}
```

Key things to remember: Objects can be allocated on the stack (automatic storage) or the heap (dynamic storage). Use `new` for heap allocation and `delete` to free memory.

Example Use Case: Creating objects to represent users, products, or any other entities in a program.

---

## Abstract Classes

What it is: A class that cannot be instantiated and is typically used as a base class. It contains at least one pure virtual function.

Why it's important: Provides a common interface for derived classes and enforces certain methods to be implemented in derived classes.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class AbstractBase {
public:
    virtual void show() = 0; // Pure virtual function
};

class Derived : public AbstractBase {
public:
    void show() override {
        std::cout << "Derived class show function called." << std::endl;
    }
};

int main() {
    Derived obj;
    obj.show();

    return 0;
}
```

Key things to remember: Pure virtual functions are declared by assigning `0` in the declaration. Abstract classes cannot be instantiated.

Example Use Case: Defining a common interface for a family of classes, such as shapes (circle, square) with a pure virtual `draw` function.

---

## Override

What it is: Providing a new implementation for a virtual function in a derived class, replacing the base class implementation.

Why it's important: Allows derived classes to customize or completely replace the behavior of virtual functions.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class Base {
public:
    virtual void show() {
        std::cout << "Base class show function called." << std::endl;
    }
};

class Derived : public Base {
public:
    void show() override { // Override the base class function
        std::cout << "Derived class show function called." << std::endl;
    }
};

int main() {
    Base* b = new Derived();
    b->show(); // Calls Derived's show() due to override

    delete b;
    return 0;
}
```

Key things to remember: Use the `override` keyword in the derived class to indicate that a function is overriding a base class virtual function. This helps catch errors at compile time.

Example Use Case: Providing a specific implementation of a function in a derived class, such as a `save` function in a `Document` class hierarchy.

---

## Structs

What it is: A `struct` is a user-defined data type in C++ that allows grouping of variables of different types under one name.

Why it's important: Provides a way to bundle related data together, similar to classes but with public access by default.

Basic syntax and usage:

C++

```cpp
#include <iostream>

struct Point {
    int x;
    int y;
};

int main() {
    Point p1; // Declare a struct variable
    p1.x = 10;
    p1.y = 20;

    std::cout << "Point coordinates: (" << p1.x << ", " << p1.y << ")" << std::endl;

    return 0;
}
```

Key things to remember: Struct members are public by default, unlike class members which are private. Structs can also have member functions, constructors, and destructors.

Example Use Case: Representing simple data structures like points, rectangles, or colors.

---

## Operator Overloading

What it is: Providing a custom implementation for an operator (like +, -, \*, etc.) for user-defined types (classes or structs).

Why it's important: Allows objects of user-defined types to be manipulated using standard operators, improving code readability and usability.

Basic syntax and usage:

C++

```cpp
#include <iostream>

class Complex {
public:
    double real;
    double imag;

    Complex(double r, double i) : real(r), imag(i) {}

    // Overload + operator
    Complex operator+(const Complex& other) {
        return Complex(real + other.real, imag + other.imag);
    }
};

int main() {
    Complex c1(1.0, 2.0);
    Complex c2(3.0, 4.0);
    Complex c3 = c1 + c2; // Uses overloaded + operator

    std::cout << "Real: " << c3.real << ", Imaginary: " << c3.imag << std::endl;

    return 0;
}
```

Key things to remember: Operator overloading functions are usually defined as member functions or friend functions. Not all operators can be overloaded, and some operators have limitations on how they can be overloaded.

Example Use Case: Overloading the + operator for a `Vector` class to allow vector addition using the standard + syntax.

---

## Lambda Expressions

What it is: A lambda expression is a concise way to define an anonymous function object (a function without a name) directly in the code.

Why it's important: Useful for short-term use when a full function definition is not required, such as in algorithms or event handling.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // Lambda expression to print each element
    std::for_each(vec.begin(), vec.end(), [](int n) {
        std::cout << n << " ";
    });
    std::cout << std::endl;

    // Lambda expression to calculate the sum
    int sum = 0;
    std::for_each(vec.begin(), vec.end(), [&sum](int n) {
        sum += n;
    });
    std::cout << "Sum: " << sum << std::endl;

    return 0;
}
```

Key things to remember: Lambda expressions can capture variables from their surrounding scope by value or by reference. The syntax is `[captures](parameters) -> return_type { body }`.

Example Use Case: Defining a custom sorting criterion for a list of objects, or handling a button click event in a GUI application.

---

## For_Each

What it is: A standard algorithm in C++ that executes a given function or lambda expression once for each element in a range (like an array or vector).

Why it's important: Provides a simple and efficient way to apply an operation to each element in a collection.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // Using a lambda expression with for_each
    std::for_each(vec.begin(), vec.end(), [](int n) {
        std::cout << n << " ";
    });
    std::cout << std::endl;

    return 0;
}
```

Key things to remember: `std::for_each` is part of the `<algorithm>` header. The function or lambda passed to `for_each` should accept a single parameter of the type contained in the range.

Example Use Case: Applying a function to each element in a container, such as printing, modifying, or calculating values.

---

## File IO

What it is: File input/output refers to the operations of reading data from and writing data to files.

Why it's important: Essential for data persistence, allowing programs to save and load data.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <fstream> // For file stream classes

int main() {
    std::ofstream outFile("example.txt"); // Create an output file stream
    outFile << "Hello, File!" << std::endl; // Write to file
    outFile.close(); // Close the file

    std::ifstream inFile("example.txt"); // Create an input file stream
    std::string line;
    while (std::getline(inFile, line)) { // Read line by line
        std::cout << line << std::endl; // Output to console
    }
    inFile.close(); // Close the file

    return 0;
}
```

Key things to remember: File streams (`std::ifstream`, `std::ofstream`, `std::fstream`) are used for file input and output. Always check if the file is open before performing operations, and close the file when done.

Example Use Case: Reading configuration settings from a file, or saving user data to a file.

---

## Functions as Objects

What it is: In C++, functions can be treated as first-class objects, meaning they can be passed as arguments to other functions, returned from functions, and assigned to variables.

Why it's important: Provides flexibility in programming, allowing functions to be used in a more dynamic and abstract way.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

void print(int n) {
    std::cout << n << " ";
}

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // Passing a function as an argument
    std::for_each(vec.begin(), vec.end(), print);
    std::cout << std::endl;

    // Returning a function from another function
    auto multiplier = [](int factor) {
        return [factor](int value) {
            return value * factor;
        };
    };

    auto timesTwo = multiplier(2);
    std::cout << "10 times 2 is " << timesTwo(10) << std::endl;

    return 0;
}
```

Key things to remember: When passing functions as arguments, ensure the parameter types match. Use `std::function` or auto keyword for type deduction when necessary.

Example Use Case: Implementing callback functions, or creating higher-order functions that return other functions.

---

## Macros

What it is: Macros are preprocessor directives in C++ that define code snippets which can be reused throughout the code. They are replaced by the preprocessor before compilation.

Why it's important: Provides a way to define reusable code snippets, constants, or to conditionally compile code.

Basic syntax and usage:

C++

```cpp
#include <iostream>

#define PI 3.14159 // Define a constant
#define SQUARE(x) ((x) * (x)) // Define a macro function

int main() {
    std::cout << "Value of PI: " << PI << std::endl;
    std::cout << "Square of 5: " << SQUARE(5) << std::endl;

    return 0;
}
```

Key things to remember: Macros are defined with `#define` and do not have a type. They are replaced by the preprocessor, so they do not follow scope or type rules.

Example Use Case: Defining constants, logging, or conditional compilation.

---

## Template Functions

What it is: A function template is a blueprint for creating a function that can operate with any data type. It is defined with template parameters.

Why it's important: Enables writing generic and reusable code that works with any data type.

Basic syntax and usage:

C++

```cpp
#include <iostream>

// Function template
template <typename T>
T add(T a, T b) {
    return a + b;
}

int main() {
    std::cout << "Integer addition: " << add(3, 4) << std::endl;
    std::cout << "Double addition: " << add(3.5, 2.5) << std::endl;

    return 0;
}
```

Key things to remember: Template functions are defined with the `template` keyword followed by template parameters. The compiler generates the function code for the specific types used.

Example Use Case: Implementing generic algorithms, such as sorting or searching, that work with any data type.

---

## Template Classes

What it is: A class template is a blueprint for creating a class that can operate with any data type. It is defined with template parameters.

Why it's important: Enables writing generic and reusable code that works with any data type at the class level.

Basic syntax and usage:

C++

```cpp
#include <iostream>

// Class template
template <typename T>
class Box {
public:
    Box(T value) : value(value) {}

    T getValue() {
        return value;
    }

private:
    T value;
};

int main() {
    Box<int> intBox(123);
    Box<double> doubleBox(456.78);

    std::cout << "Integer box: " << intBox.getValue() << std::endl;
    std::cout << "Double box: " << doubleBox.getValue() << std::endl;

    return 0;
}
```

Key things to remember: Template classes are defined with the `template` keyword followed by template parameters. The compiler generates the class code for the specific types used.

Example Use Case: Implementing generic data structures, such as linked lists, stacks, or queues, that work with any data type.

---

## Double Ended Queue

What it is: A double-ended queue (deque) is a sequence container that allows fast insertion and deletion at both its beginning and end.

Why it's important: Provides the functionality of both stacks and queues, allowing elements to be added or removed from both ends.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <deque>

int main() {
    std::deque<int> dq;

    // Inserting elements at both ends
    dq.push_front(10);
    dq.push_back(20);

    // Removing elements from both ends
    dq.pop_front();
    dq.pop_back();

    return 0;
}
```

Key things to remember: Deques are part of the Standard Template Library (STL) and are defined in the `<deque>` header. They provide random access to elements and are implemented as a dynamic array.

Example Use Case: Implementing a task scheduler where tasks can be added or removed from both ends of the queue.

---

## Iterators

What it is: Iterators are objects that allow traversing through the elements of a container (like arrays, vectors, lists) without exposing the underlying structure.

Why it's important: Provide a uniform way to access and traverse elements in different types of containers.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // Using an iterator to traverse the vector
    for (std::vector<int>::iterator it = vec.begin(); it != vec.end(); ++it) {
        std::cout << *it << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

Key things to remember: Iterators are similar to pointers and support operations like increment (++), dereference (\*), and comparison (!=). Use `auto` keyword for type deduction in range-based for loops.

Example Use Case: Traversing and modifying elements in a container, such as applying a function to each element.

---

## Malloc/Memory Management

What it is: `malloc` is a C standard library function for allocating a specified amount of memory during program execution. Memory management refers to the process of allocating, using, and freeing memory in a program.

Why it's important: Dynamic memory allocation allows programs to use memory more efficiently and flexibly. Proper memory management is crucial to avoid memory leaks and ensure optimal performance.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <cstdlib> // For malloc and free

int main() {
    // Allocate memory for an array of 10 integers
    int* arr = (int*)malloc(10 * sizeof(int));

    // Use the allocated memory...

    // Free the allocated memory
    free(arr);

    return 0;
}
```

Key things to remember: Use `malloc` to allocate memory and `free` to deallocate memory. Always check if the memory allocation was successful (malloc returns NULL on failure).

Example Use Case: Allocating memory for a dynamic array whose size is not known at compile time.

---

## Smart Pointers

What it is: Smart pointers are objects that act like pointers but provide automatic memory management. They ensure that memory is properly released when it is no longer needed.

Why it's important: Help prevent memory leaks and dangling pointers by automatically managing the lifetime of the allocated memory.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <memory> // For smart pointers

int main() {
    // Create a smart pointer
    std::unique_ptr<int> ptr(new int(42));

    // Use the smart pointer
    std::cout << *ptr << std::endl;

    // No need to explicitly free the memory

    return 0;
}
```

Key things to remember: Smart pointers are defined in the `<memory>` header. `std::unique_ptr` represents exclusive ownership of an object, and `std::shared_ptr` represents shared ownership.

Example Use Case: Managing the lifetime of dynamically allocated objects, such as in a factory function or a resource manager.

---

## Threads

What it is: Threads are the smallest unit of processing that can be scheduled by an operating system. A thread is a sequence of instructions that can be executed independently.

Why it's important: Multithreading allows concurrent execution of code, improving the performance and responsiveness of applications.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <thread>

void function1() {
    std::cout << "Function 1 is running." << std::endl;
}

void function2(int x) {
    std::cout << "Function 2 received: " << x << std::endl;
}

int main() {
    // Create and run threads
    std::thread t1(function1);
    std::thread t2(function2, 10);

    // Wait for threads to complete
    t1.join();
    t2.join();

    return 0;
}
```

Key things to remember: Threads are created with the `std::thread` class. Use `.join()` to wait for a thread to complete. Be cautious of data races and use synchronization mechanisms (like mutexes) when accessing shared data.

Example Use Case: Performing background tasks, such as loading resources or processing data, without blocking the main thread.

---

## Time Functions

What it is: Functions that provide the current time and date, and allow measuring time intervals.

Why it's important: Useful for profiling code, measuring performance, and timestamping events.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <chrono>

int main() {
    // Get the current time
    auto now = std::chrono::system_clock::now();
    std::time_t now_c = std::chrono::system_clock::to_time_t(now);
    std::cout << "Current time: " << std::ctime(&now_c);

    // Measure the time taken by a code block
    auto start = std::chrono::high_resolution_clock::now();
    // Code block...
    auto end = std::chrono::high_resolution_clock::now();
    std::chrono::duration<double> duration = end - start;
    std::cout << "Duration: " << duration.count() << " seconds." << std::endl;

    return 0;
}
```

Key things to remember: Time functions are defined in the `<chrono>` header. Use `std::chrono::system_clock` for wall-clock time and `std::chrono::high_resolution_clock` for high-resolution timing.

Example Use Case: Measuring the execution time of a function or a code block, or getting the current timestamp for logging.

---

## Lists

What it is: A list is a sequence container that allows non-contiguous memory allocation and provides bidirectional iterators.

Why it's important: Efficient for inserting and removing elements from anywhere in the container.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <list>

int main() {
    std::list<int> myList;

    // Inserting elements
    myList.push_back(10);
    myList.push_front(20);

    // Removing elements
    myList.pop_back();
    myList.pop_front();

    return 0;
}
```

Key things to remember: Lists are part of the Standard Template Library (STL) and are defined in the `<list>` header. They provide bidirectional iterators and are implemented as a doubly linked list.

Example Use Case: Implementing a playlist of songs where songs can be added or removed from both ends.

---

## Forward List

What it is: A forward list is a sequence container that allows non-contiguous memory allocation and provides single-directional iterators.

Why it's important: More memory-efficient than a list when only forward traversal is needed.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <forward_list>

int main() {
    std::forward_list<int> myFwdList;

    // Inserting elements
    myFwdList.push_front(10);
    myFwdList.push_front(20);

    // Removing elements
    myFwdList.pop_front();

    return 0;
}
```

Key things to remember: Forward lists are part of the Standard Template Library (STL) and are defined in the `<forward_list>` header. They provide single-directional iterators and are implemented as a singly linked list.

Example Use Case: Implementing a simple undo feature where only the last action needs to be remembered.

---

## Sets

What it is: A set is an associative container that contains a sorted collection of unique objects of type Key.

Why it's important: Efficient for checking the existence of an element, and for operations like union, intersection, and difference.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <set>

int main() {
    std::set<int> mySet;

    // Inserting elements
    mySet.insert(10);
    mySet.insert(20);

    // Removing elements
    mySet.erase(10);

    return 0;
}
```

Key things to remember: Sets are part of the Standard Template Library (STL) and are defined in the `<set>` header. They store unique elements following a specific order.

Example Use Case: Storing a collection of unique tags or keywords.

---

## Multisets

What it is: A multiset is an associative container that contains a sorted collection of objects of type Key, allowing multiple equivalent elements.

Why it's important: Useful when duplicates are allowed and need to be counted or accessed in a sorted manner.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <set>

int main() {
    std::multiset<int> myMultiSet;

    // Inserting elements
    myMultiSet.insert(10);
    myMultiSet.insert(20);
    myMultiSet.insert(10); // Duplicate value

    // Removing elements
    myMultiSet.erase(10);

    return 0;
}
```

Key things to remember: Multisets are part of the Standard Template Library (STL) and are defined in the `<set>` header. They allow multiple occurrences of the same element.

Example Use Case: Storing a collection of votes or ratings where multiple identical values are possible.

---

## Map

What it is: A map is an associative container that contains a sorted collection of key-value pairs, with unique keys.

Why it's important: Efficient for retrieving, inserting, and removing key-value pairs based on the key.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <map>

int main() {
    std::map<int, std::string> myMap;

    // Inserting elements
    myMap.insert(std::pair<int, std::string>(1, "One"));
    myMap[2] = "Two"; // Another way to insert

    // Accessing elements
    std::cout << "Key 1: " << myMap.at(1) << std::endl;

    // Removing elements
    myMap.erase(2);

    return 0;
}
```

Key things to remember: Maps are part of the Standard Template Library (STL) and are defined in the `<map>` header. They store key-value pairs with unique keys, following a specific order.

Example Use Case: Storing a phone book where names are keys and phone numbers are values.

---

## Multimaps

What it is: A multimap is an associative container that contains a sorted collection of key-value pairs, allowing multiple equivalent keys.

Why it's important: Useful when a single key is associated with multiple values and needs to be accessed in a sorted manner.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <map>

int main() {
    std::multimap<int, std::string> myMultiMap;

    // Inserting elements
    myMultiMap.insert(std::pair<int, std::string>(1, "One"));
    myMultiMap.insert(std::pair<int, std::string>(1, "Uno")); // Duplicate key
    myMultiMap.insert(std::pair<int, std::string>(2, "Two"));

    // Accessing elements
    for (const auto& pair : myMultiMap) {
        std::cout << "Key " << pair.first << ": " << pair.second << std::endl;
    }

    // Removing elements
    myMultiMap.erase(1);

    return 0;
}
```

Key things to remember: Multimaps are part of the Standard Template Library (STL) and are defined in the `<map>` header. They allow multiple occurrences of the same key.

Example Use Case: Storing a collection of books where each author (key) can have multiple books (values).

---

## Stack

What it is: A stack is a container that follows the Last In First Out (LIFO) principle, where the last element added is the first one to be removed.

Why it's important: Useful for managing data in a specific order, such as undo mechanisms, parsing expressions, or backtracking algorithms.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <stack>

int main() {
    std::stack<int> myStack;

    // Pushing elements onto the stack
    myStack.push(10);
    myStack.push(20);

    // Popping elements from the stack
    myStack.pop();

    return 0;
}
```

Key things to remember: Stacks are part of the Standard Template Library (STL) and are defined in the `<stack>` header. They provide restricted access to elements (only top element is accessible).

Example Use Case: Implementing a browser's back button functionality.

---

## Queue

What it is: A queue is a container that follows the First In First Out (FIFO) principle, where the first element added is the first one to be removed.

Why it's important: Useful for managing data in the order it was received, such as print jobs, task scheduling, or breadth-first search algorithms.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <queue>

int main() {
    std::queue<int> myQueue;

    // Enqueuing elements
    myQueue.push(10);
    myQueue.push(20);

    // Dequeuing elements
    myQueue.pop();

    return 0;
}
```

Key things to remember: Queues are part of the Standard Template Library (STL) and are defined in the `<queue>` header. They provide restricted access to elements (only front and back elements are accessible).

Example Use Case: Implementing a print queue where documents are printed in the order they are received.

---

## Priority Queues

What it is: A priority queue is an abstract data type that operates similar to a regular queue or stack data structure, but where additionally each element has a "priority" associated with it.

Why it's important: Allows processing of elements based on their priority rather than just their order in the queue.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <queue>

int main() {
    // Create a priority queue with default less-than comparison (max-heap)
    std::priority_queue<int> myPQ;

    // Inserting elements
    myPQ.push(10);
    myPQ.push(20);
    myPQ.push(15);

    // Accessing the top element (highest priority)
    std::cout << "Top element: " << myPQ.top() << std::endl;

    // Removing the top element
    myPQ.pop();

    return 0;
}
```

Key things to remember: Priority queues are part of the Standard Template Library (STL) and are defined in the `<queue>` header. By default, they are implemented as max-heaps (highest priority first).

Example Use Case: Managing tasks in a task manager where some tasks have higher priority than others.

---

## Enums

What it is: An enum (enumeration) is a user-defined type in C++ that consists of a set of named integral constants.

Why it's important: Provides a way to define and group related constants with a meaningful name, improving code readability.

Basic syntax and usage:

C++

```cpp
#include <iostream>

// Define an enum for days of the week
enum class Day { Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };

int main() {
    Day today = Day::Monday;

    if (today == Day::Monday) {
        std::cout << "Start of the work week!" << std::endl;
    }

    return 0;
}
```

Key things to remember: Enums are defined using the `enum` keyword, followed by the enum name and enumerators. Scoped enums (enum class) provide better type safety and scoping.

Example Use Case: Defining a set of states for a traffic light (red, yellow, green) or days of the week.

---

## Regular Expressions

What it is: Regular expressions (regex) are sequences of characters that define a search pattern, mainly for use in pattern matching with strings.

Why it's important: Provides a powerful and flexible way to search, match, and manipulate strings based on patterns.

Basic syntax and usage:

C++

```cpp
#include <iostream>
#include <regex>

int main() {
    std::string text = "The rain in Spain stays mainly in the plain.";
    std::regex pattern("ain");

    // Search for the pattern in the text
    if (std::regex_search(text, pattern)) {
        std::cout << "Pattern found!" << std::endl;
    }

    return 0;
}
```

Key things to remember: Regular expressions are defined in the `<regex>` header. Use `std::regex` to define a regex pattern, and functions like `std::regex_search`, `std::regex_match`, and `std::regex_replace` to perform operations.

Example Use Case: Validating input formats (like email or phone number), searching and replacing text, or parsing structured text data.
