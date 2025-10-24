# Python Cheatsheet

---

## Python Basics

- **Print:**
  ```python
  print("Hello, world!")
  ```
- **Run:** `python file.py`
- **Key:** Indentation matters (4 spaces).

---

## Variables

- **Assign:**
  ```python
  age = 30
  name = "Alice"
  is_student = True
  ```
- **Key:** No type declaration needed.

---

## Type Casting

- **Convert:**
  ```python
  n = int("10")
  s = str(10)
  f = float("3.14")
  ```
- **Key:** `input()` returns string.

---

## User Input

- **Read:**
  ```python
  name = input("Name? ")
  ```
- **Key:** Always string; cast if needed.

---

## Arithmetic & Math

- **Operators:** `+ - * / // % **`
- **Math module:**
  ```python
  import math
  math.sqrt(16)
  math.pi
  ```
- **Key:** Use `math` for advanced ops.

---

## If / Elif / Else

- **Syntax:**
  ```python
  if x > 0:
      ...
  elif x == 0:
      ...
  else:
      ...
  ```
- **Key:** Indentation defines blocks.

---

## Logical Operators

- **Combine:** `and`, `or`, `not`
- **Example:**
  ```python
  if a > 0 and b < 10:
      ...
  ```

---

## Ternary (Conditional Expression)

- **Syntax:**
  ```python
  result = "yes" if cond else "no"
  ```

---

## Strings

- **Methods:**
  ```python
  s = " hi "
  s.strip().upper()
  s[0:2]
  f"Hello {name}"
  ```
- **Key:** Strings are immutable.

---

## While / For Loops

- **While:**
  ```python
  while cond:
      ...
  ```
- **For:**
  ```python
  for x in [1,2,3]:
      ...
  for i in range(5):
      ...
  ```
- **Key:** Use `break`/`continue` as needed.

---

## Lists, Tuples, Sets

- **List:**
  ```python
  l = [1, 2, 3]
  l.append(4)
  ```
- **Tuple:**
  ```python
  t = (1, 2, 3)
  ```
- **Set:**
  ```python
  s = {1, 2, 3}
  s.add(4)
  ```
- **Key:** List = mutable, Tuple = immutable, Set = unique.

---

## Dictionaries

- **Create & Access:**
  ```python
  d = {"a": 1, "b": 2}
  d["a"]
  d.get("c", 0)
  ```
- **Key:** Keys must be unique.

---

## List Comprehensions

- **Syntax:**
  ```python
  squares = [x*x for x in range(5)]
  evens = [x for x in range(10) if x%2==0]
  ```

---

## Functions

- **Define/Call:**
  ```python
  def add(a, b=0):
      return a + b
  add(2, 3)
  ```
- **Args/kwargs:**
  ```python
  def f(*args, **kwargs): pass
  ```
- **Key:** Use `return` for output.

---

## Membership & Iterables

- **Check:**
  ```python
  if "a" in ["a", "b"]:
      ...
  ```
- **Iterate:**
  ```python
  for item in iterable:
      ...
  ```

---

## Match-Case (Python 3.10+)

- **Syntax:**
  ```python
  match x:
      case 1: ...
      case _: ...
  ```

---

## Modules & Imports

- **Import:**
  ```python
  import math
  from random import randint
  import numpy as np
  ```
- **Key:** Use `import` to reuse code.

---

## Scope (LEGB)

- **Order:** Local, Enclosing, Global, Built-in.
- **Key:** Use `global` or `nonlocal` to modify outer variables.

---

## Main Guard

- **Syntax:**
  ```python
  if __name__ == "__main__":
      main()
  ```

---

## OOP: Classes & Objects

- **Define:**
  ```python
  class Car:
      def __init__(self, make):
          self.make = make
      def drive(self):
          print(f"{self.make} drives")
  c = Car("Toyota")
  c.drive()
  ```
- **Key:** Use `self` for instance vars.

---

## Inheritance & super()

- **Syntax:**
  ```python
  class Dog(Animal):
      def __init__(self):
          super().__init__()
  ```
- **Key:** Child inherits parent methods.

---

## Static & Class Methods

- **Static:**
  ```python
  @staticmethod
  def foo(): ...
  ```
- **Class:**
  ```python
  @classmethod
  def bar(cls): ...
  ```

---

## Magic Methods (Dunders)

- **Example:**
  ```python
  def __str__(self): ...
  def __add__(self, other): ...
  ```

---

## @property

- **Syntax:**
  ```python
  @property
  def area(self): ...
  ```

---

## Decorators

- **Syntax:**
  ```python
  def deco(f): ...
  @deco
  def foo(): ...
  ```

---

## Exception Handling

- **Syntax:**
  ```python
  try:
      ...
  except Exception as e:
      ...
  else:
      ...
  finally:
      ...
  ```

---

## File IO

- **Write:**
  ```python
  with open("f.txt", "w") as f:
      f.write("hi")
  ```
- **Read:**
  ```python
  with open("f.txt") as f:
      data = f.read()
  ```

---

## Dates & Times

- **Syntax:**
  ```python
  from datetime import datetime
  now = datetime.now()
  now.strftime("%Y-%m-%d")
  ```

---

## Random

- **Syntax:**
  ```python
  import random
  random.randint(1, 6)
  random.choice([1,2,3])
  ```

---

## Multithreading

- **Syntax:**
  ```python
  import threading
  t = threading.Thread(target=func)
  t.start(); t.join()
  ```

---

## HTTP Requests

- **Syntax:**
  ```python
  import requests
  r = requests.get(url)
  if r.status_code == 200:
      data = r.json()
  ```

---

## Testing

- **Syntax:**
  ```python
  import unittest
  class TestX(unittest.TestCase):
      def test_add(self):
          self.assertEqual(add(1,2), 3)
  if __name__ == "__main__":
      unittest.main()
  ```

---

## PyQt5 GUI (Basics)

- **Syntax:**
  ```python
  from PyQt5.QtWidgets import QApplication, QWidget
  app = QApplication([])
  win = QWidget()
  win.show()
  app.exec_()
  ```

---
