# Dart Cheatsheet

## Basic Syntax

**What it is:** Core elements of Dart programming language.

**Basic syntax:**

```dart
void main() {
  print("Hello World!"); // Print to console
}
```

## Variables and Data Types

```dart
// Type declarations
int x = 2;            // explicitly typed
var p = 5;            // type inferred
dynamic z = 8;        // variable can take any type
final email = "test@example.com";  // cannot be reassigned
const qty = 5;        // compile-time constant

// Data types
int age = 20;
double height = 1.85;
num x = 1;           // can be int or double
String name = "Dart";
bool isActive = true;

// String interpolation
var firstName = 'John';
var lastName = "Doe";
String fullName = "$firstName $lastName";
String upperCase = '${firstName.toUpperCase()}';
```

## Operators

```dart
// Arithmetic
print(2 + 3);    // Addition: 5
print(5 / 2);    // Division: 2.5
print(5 ~/ 2);   // Integer division: 2
print(5 % 2);    // Modulo: 1

// Increment/Decrement
int a = 1;
++a;  // pre-increment
a++;  // post-increment

// Comparison
print(2 == 2);   // Equal
print(2 != 3);   // Not Equal
print(3 > 2);    // Greater than

// Logical
bool isValid = !false;         // NOT
bool result = true && false;   // AND
bool other = true || false;    // OR
```

## Control Flow

```dart
// If-else
if (age < 18) {
  print("Teen");
} else if (age < 60) {
  print("Adult");
} else {
  print("Senior");
}

// Switch
switch(value) {
  case 1:
    print('One');
    break;
  default:
    print('Other');
}

// Loops
while (!isDone) {
  doWork();
}

do {
  tryAgain();
} while (!success);

for (var i = 0; i < 5; i++) {
  print(i);
}

for (var item in items) {
  print(item);
}
```

## Collections

```dart
// Lists
var list = [1, 2, 3];
List<String> cities = ["New York", "London"];

// Sets
var uniqueNumbers = {1, 2, 3};
Set<String> names = {};

// Maps
var person = {
  'name': 'John',
  'age': 30
};
Map<String, int> scores = {};
```

## Functions

```dart
// Basic function
int add(int a, int b) {
  return a + b;
}

// Arrow syntax
bool isEven(int n) => n % 2 == 0;

// Optional parameters
void greet([String name = 'Guest']) {
  print('Hello, $name!');
}

// Named parameters
void createUser({
  required String name,
  int age = 0
}) {
  // ...
}
```

## Classes and Objects

```dart
class Person {
  String name;
  int age;

  // Constructor
  Person(this.name, this.age);

  // Named constructor
  Person.guest() : name = 'Guest', age = 0;

  // Method
  void introduce() {
    print('I am $name, $age years old');
  }

  // Getter
  String get info => '$name ($age)';

  // Setter
  set userAge(int value) {
    if (value >= 0) age = value;
  }
}
```

## Async Programming

```dart
// Future
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2));
  return 'Data loaded';
}

// Using await
void loadData() async {
  print('Loading...');
  var result = await fetchData();
  print(result);
}
```

## Error Handling

```dart
try {
  var result = someRiskyOperation();
} on SpecificException {
  print('Specific error handled');
} catch (e) {
  print('Error: $e');
} finally {
  cleanup();
}
```

## Null Safety

```dart
// Nullable variables
String? nullableName;
int? age;

// Non-null assertion
String name = nullableName!;  // Throws if null

// Null-aware operators
var display = nullableName ?? 'Guest';  // Default value if null
nullableName ??= 'New Guest';  // Assign if null
```
