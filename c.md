# C Programming Fundamentals Cheatsheet

---

## Introduction to C Programming ⚙

- **What:** Procedural, low-level, foundational language.
- **Why:** Powers OS kernels, teaches how computers work.
- **Syntax:**
  ```c
  #include <stdio.h>
  int main(void) {
      printf("Hello, World!\n");
      return 0;
  }
  ```
- **Key:** Case-sensitive, semicolons, `main` is entry, `#include` for libraries.

---

## Variables ❎

- **What:** Named memory for data.
- **Why:** Store and manipulate values.
- **Syntax:**
  ```c
  int age = 20;
  double price;
  char letter = 'A';
  ```
- **Key:** Declare before use, type can't change.

---

## Format Specifiers 🛠

- **What:** Placeholders for printf/scanf.
- **Why:** Correctly format input/output.
- **Syntax:** `%d` (int), `%f` (float), `%lf` (double), `%c` (char), `%s` (string)
- **Example:**
  ```c
  printf("Age: %d\n", age);
  ```

---

## Arithmetic Operators ➗

- **What:** +, -, \*, /, %
- **Why:** Math and logic.
- **Syntax:**
  ```c
  int sum = a + b;
  int rem = a % b;
  ```
- **Key:** Integer division truncates, `%` only for ints.

---

## User Input ⌨

- **What:** Read from keyboard.
- **Why:** Interactive programs.
- **Syntax:**
  ```c
  int age;
  scanf("%d", &age);
  ```
- **Key:** Use `&` for non-string variables.

---

## Math Functions 🧮

- **What:** Common math ops from `<math.h>`.
- **Why:** Accurate, optimized calculations.
- **Syntax:**
  ```c
  #include <math.h>
  double r = sqrt(9.0);
  double p = pow(2.0, 3.0);
  ```
- **Key:** Link with `-lm` when compiling.

---

## If Statements 🤔

- **What:** Conditional logic.
- **Why:** Control flow.
- **Syntax:**
  ```c
  if (x > 0) { ... } else { ... }
  ```
- **Key:** Use `==` for equality.

---

## Switches 💡

- **What:** Multi-way branch.
- **Why:** Cleaner than many if-else.
- **Syntax:**
  ```c
  switch (val) {
      case 1: ...; break;
      default: ...;
  }
  ```
- **Key:** Use `break` to prevent fall-through.

---

## Logical Operators ❗

- **What:** Combine conditions: `&&`, `||`, `!`
- **Why:** Complex decisions.
- **Syntax:**
  ```c
  if (a > 0 && b < 10) { ... }
  ```
- **Key:** `&&` (AND), `||` (OR), `!` (NOT).

---

## Functions 📞

- **What:** Reusable code blocks.
- **Why:** Modularity, reuse.
- **Syntax:**
  ```c
  int add(int a, int b) { return a + b; }
  ```
- **Key:** Declare before use (prototype or definition).

---

## Return 🔙

- **What:** Exit function, optionally return value.
- **Syntax:**
  ```c
  return result;
  ```
- **Key:** Type must match function's return type.

---

## Variable Scope 🏠

- **What:** Where a variable is accessible.
- **Why:** Prevents conflicts.
- **Syntax:**
  ```c
  int global = 1;
  void foo() { int local = 2; }
  ```
- **Key:** Local inside function/block, global outside.

---

## Function Prototypes 📌

- **What:** Declare function before use.
- **Why:** Allows calling before definition.
- **Syntax:**
  ```c
  int add(int, int);
  ```
- **Key:** Place at top or in header file.

---

## Loops (while, for) 🔂

- **What:** Repeat code.
- **Why:** Process collections, repeat tasks.
- **Syntax:**
  ```c
  while (cond) { ... }
  for (int i = 0; i < n; i++) { ... }
  ```
- **Key:** For known or unknown iterations.

---

## Break & Continue 🛑

- **What:** Control loop flow.
- **Why:** Exit or skip iterations.
- **Syntax:**
  ```c
  if (x == 3) continue;
  if (x == 7) break;
  ```
- **Key:** `break` exits loop, `continue` skips to next.

---

## Arrays 🗃

- **What:** Fixed-size, same-type collection.
- **Why:** Store related data.
- **Syntax:**
  ```c
  int arr[5] = {1,2,3,4,5};
  arr[0] = 10;
  ```
- **Key:** Zero-indexed, fixed size.

---

## 2D Arrays ⬜

- **What:** Array of arrays (matrix).
- **Why:** Tabular data.
- **Syntax:**
  ```c
  int mat[2][3] = {{1,2,3},{4,5,6}};
  ```
- **Key:** Access as `mat[row][col]`.

---

## Strings & Arrays of Strings 🧵

- **What:** Array of chars, or array of char arrays.
- **Why:** Store text, lists of text.
- **Syntax:**
  ```c
  char s[10] = "hello";
  char names[3][10] = {"A", "B", "C"};
  ```
- **Key:** `%s` for printf, null-terminated.

---

## Ternary Operator ❓

- **What:** Shorthand if-else.
- **Syntax:**
  ```c
  int max = (a > b) ? a : b;
  ```
- **Key:** Use for simple assignments.

---

## Typedef 📛

- **What:** Type alias.
- **Why:** Readability, convenience.
- **Syntax:**
  ```c
  typedef unsigned long ulong;
  ```
- **Key:** Often used for structs.

---

## Enums 📅

- **What:** Named integer constants.
- **Why:** Readable code, fixed options.
- **Syntax:**
  ```c
  enum Day { SUN, MON, TUE };
  enum Day today = MON;
  ```
- **Key:** Values start at 0 by default.

---

## Structs 📦

- **What:** Group variables of different types.
- **Why:** Model real-world entities.
- **Syntax:**
  ```c
  struct Person { char name[20]; int age; };
  struct Person p;
  p.age = 30;
  ```
- **Key:** Access with dot (`.`).

---

## Arrays of Structs 🗄

- **What:** List of records.
- **Syntax:**
  ```c
  struct Car { char model[10]; int year; };
  struct Car garage[3];
  ```
- **Key:** Access as `garage[i].year`.

---

## Pointers 👈

- **What:** Store memory addresses.
- **Why:** Dynamic memory, efficient passing.
- **Syntax:**
  ```c
  int x = 5;
  int *p = &x;
  printf("%d", *p);
  ```
- **Key:** `*` for pointer/dereference, `&` for address.

---

## Random Numbers 🎲

- **What:** Generate pseudo-random values.
- **Syntax:**
  ```c
  #include <stdlib.h>
  #include <time.h>
  srand(time(NULL));
  int r = (rand() % 6) + 1;
  ```
- **Key:** Seed once with `srand`.

---

## File IO (Write/Read) ✍📖

- **What:** Save/load data to/from files.
- **Syntax:**
  ```c
  FILE *f = fopen("file.txt", "w");
  fprintf(f, "hi");
  fclose(f);
  ```
- **Key:** Always check for NULL, close files.

---

## Malloc/Calloc/Realloc/Free 🏢🧹🚢

- **What:** Dynamic memory allocation.
- **Why:** Flexible data structures.
- **Syntax:**
  ```c
  int *p = malloc(n * sizeof(int));
  int *q = calloc(n, sizeof(int));
  p = realloc(p, new_size * sizeof(int));
  free(p);
  ```
- **Key:** Always free after use, check for NULL.

---
