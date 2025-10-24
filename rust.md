# Rust Programming Cheatsheet

---

## Create Project

- **What:** Use Cargo to create/manage projects.
- **Why:** Handles builds, dependencies, structure.
- **Syntax:**
  ```bash
  cargo new my_project
  cargo run
  ```
- **Key:** Always start with `cargo new`.

---

## Cargo.toml & Dependencies

- **What:** Project config and dependency list.
- **Why:** Manage metadata and external crates.
- **Syntax:**
  ```toml
  [package]
  name = "my_app"
  version = "0.1.0"
  [dependencies]
  rand = "0.8.5"
  ```
- **Key:** Add dependencies here, use `cargo update` to refresh.

---

## Main Function

- **What:** Program entry point.
- **Syntax:**
  ```rust
  fn main() {
      println!("Hello, Rust!");
  }
  ```
- **Key:** Every binary needs `fn main()`.

---

## Variables & Mutability

- **What:** Store data, immutable by default.
- **Syntax:**
  ```rust
  let x = 5;
  let mut y = 10;
  y = 20;
  ```
- **Key:** Use `mut` for mutability.

---

## Constants & Shadowing

- **What:**
  - `const`: Compile-time, always type-annotated.
  - Shadowing: Reuse variable name.
- **Syntax:**
  ```rust
  const PI: f64 = 3.14;
  let x = 5;
  let x = x + 1; // shadows previous x
  ```
- **Key:** `const` is global, shadowing can change type.

---

## Data Types

- **What:** Integers, floats, bool, char, tuples, arrays.
- **Syntax:**
  ```rust
  let n: i32 = 10;
  let f: f64 = 3.14;
  let b: bool = true;
  let c: char = 'R';
  let tup = (1, 2.0, 'a');
  let arr = [1, 2, 3];
  ```
- **Key:** Types are explicit or inferred.

---

## Input & Output

- **What:** Read from stdin, print to stdout.
- **Syntax:**
  ```rust
  use std::io;
  let mut s = String::new();
  io::stdin().read_line(&mut s).unwrap();
  println!("{}", s.trim());
  ```
- **Key:** Input is always a String; parse as needed.

---

## Math & Random

- **What:** Arithmetic, random numbers.
- **Syntax:**
  ```rust
  let sum = 5 + 3;
  use rand::Rng;
  let n: u32 = rand::thread_rng().gen_range(1..=10);
  ```
- **Key:** Add `rand` to dependencies for randomness.

---

## If, Match, Ternary

- **What:** Control flow.
- **Syntax:**
  ```rust
  if x > 0 { ... } else { ... }
  let y = if cond { 1 } else { 2 };
  match val {
      1 => ...,
      _ => ...,
  }
  ```
- **Key:** `if` is an expression; `match` is exhaustive.

---

## Loops

- **What:** Repeat code.
- **Syntax:**
  ```rust
  loop { ... }
  while cond { ... }
  for x in arr.iter() { ... }
  ```
- **Key:** Use `break`/`continue` to control flow.

---

## Arrays, Vectors, Tuples

- **What:** Collections.
- **Syntax:**
  ```rust
  let arr = [1,2,3];
  let mut v = vec![1,2,3];
  let t = (1, "hi");
  ```
- **Key:** Arrays fixed size, vectors growable.

---

## Strings

- **What:** `String` (owned, growable), `&str` (slice).
- **Syntax:**
  ```rust
  let s = String::from("hi");
  let s2 = &s[0..2];
  ```
- **Key:** Use `.push_str()`, `.to_string()`, `.chars()` for manipulation.

---

## Functions

- **What:** Reusable code blocks.
- **Syntax:**
  ```rust
  fn add(a: i32, b: i32) -> i32 { a + b }
  ```
- **Key:** Type annotations required.

---

## Ownership & Borrowing

- **What:** Memory safety rules.
- **Syntax:**
  ```rust
  let s = String::from("hi");
  let s2 = s; // s moved, can't use s
  let s3 = s2.clone(); // deep copy
  fn foo(x: &String) { ... } // borrow
  ```
- **Key:** Only one owner; use `&` for borrowing.

---

## Structs & Enums

- **What:** Custom types.
- **Syntax:**
  ```rust
  struct User { name: String }
  enum Color { Red, Green, Blue }
  ```
- **Key:** Use `impl` for methods.

---

## Traits

- **What:** Shared behavior (like interfaces).
- **Syntax:**
  ```rust
  trait Speak { fn speak(&self); }
  impl Speak for User { fn speak(&self) { ... } }
  ```
- **Key:** Use `impl Trait` or generics for trait bounds.

---

## HashMap

- **What:** Key-value store.
- **Syntax:**
  ```rust
  use std::collections::HashMap;
  let mut m = HashMap::new();
  m.insert("a", 1);
  let v = m.get("a");
  ```
- **Key:** Keys must be hashable.

---

## Error Handling

- **What:** Use `Result` and `Option`.
- **Syntax:**
  ```rust
  fn foo() -> Result<(), String> { Ok(()) }
  let res = foo();
  match res {
      Ok(_) => ...,
      Err(e) => ...,
  }
  ```
- **Key:** Use `?` to propagate errors.

---

## File IO

- **What:** Read/write files.
- **Syntax:**
  ```rust
  use std::fs::File;
  let mut f = File::create("out.txt")?;
  use std::io::Write;
  f.write_all(b"hi")?;
  ```
- **Key:** Handle errors with `Result`.

---

## Iterators & Closures

- **What:** Process collections, anonymous functions.
- **Syntax:**
  ```rust
  let v = vec![1,2,3];
  let sum: i32 = v.iter().map(|x| x*2).sum();
  ```
- **Key:** Closures: `|x| x+1`.

---

## Smart Pointers

- **What:** Heap allocation, shared ownership.
- **Syntax:**
  ```rust
  let b = Box::new(5);
  use std::rc::Rc;
  let r = Rc::new(5);
  ```
- **Key:** `Box` for heap, `Rc` for shared single-threaded.

---

## Modules

- **What:** Organize code.
- **Syntax:**
  ```rust
  mod foo { pub fn bar() {} }
  use crate::foo::bar;
  ```
- **Key:** Use `pub` for visibility.

---

## Concurrency & Threads

- **What:** Run code in parallel.
- **Syntax:**
  ```rust
  use std::thread;
  thread::spawn(|| { ... }).join().unwrap();
  ```
- **Key:** Use `move` to transfer ownership to threads.

---

## Installation

- **What:** Install Rust toolchain.
- **How:**
  ```bash
  curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
  rustc --version
  cargo --version
  ```
- **Key:** Use `cargo` for building and running.
