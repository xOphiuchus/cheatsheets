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

## Ownership & Borrowing (expanded)

- **What it is:** Rust's memory model: each value has one owner; moving transfers ownership; borrowing allows non-owning access.
- **Why it's important:** Prevents data races and dangling pointers at compile time using the borrow checker.

**Basic rules:**

1. Each value has a single owner.
2. When the owner goes out of scope, value is dropped.
3. Move transfers ownership; some types (Copy) are copied instead.
4. You can borrow immutably many times, or mutably once. Not both simultaneously.

**Examples:**

```rust
// Move semantics
fn take_ownership(s: String) { println!("took: {}", s); }
let s = String::from("hello");
take_ownership(s); // s is moved; cannot use s afterward

// Clone to duplicate data
let s1 = String::from("hi");
let s2 = s1.clone(); // deep copy; s1 still usable

// Borrowing (immutable)
fn len(s: &String) -> usize { s.len() }
let s = String::from("hello");
let l = len(&s); // s not moved

// Mutable borrow
fn append_excl(s: &mut String) { s.push('!'); }
let mut s = String::from("hi");
append_excl(&mut s);
```

**Key things to remember:**

- Primitive types (ints, bools) implement Copy and are copied rather than moved.
- The borrow checker enforces lifetimes; avoid returning references to local variables.
- Lifetimes annotate relationships; e.g., `fn longest<'a>(x: &'a str, y: &'a str) -> &'a str`

**Example use case:** Prevents dangling refs and enforces safe memory usage without GC.

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

## Error Handling (small addition)

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

**Example:**

```rust
use std::fs::File;
use std::io::{self, Read};

fn read_file() -> io::Result<String> {
    let mut f = File::open("file.txt")?;
    let mut s = String::new();
    f.read_to_string(&mut s)?;
    Ok(s)
}
```

**Key things to remember:** `?` returns early on `Err` and converts types where needed.

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

## Concurrency & Threads (expanded)

- **What it is:** Run work in parallel via threads; Rust enforces safety using ownership rules and marker traits `Send` and `Sync`.
- **Why it's important:** Safe concurrency by design prevents data races at compile time.

**Move closures and join:**

```rust
use std::thread;

let name = String::from("rustacean");
let handle = thread::spawn(move || { // move transfers ownership into closure
    println!("Hello {}", name);
});
handle.join().unwrap();
```

**Why `move`?**

- The spawned closure must own (or be 'static' for) values it uses because the original scope may end before the thread completes. `move` moves ownership into the closure so the closure can outlive the spawning scope.

**Shared mutability with Arc and Mutex:**

```rust
use std::sync::{Arc, Mutex};
use std::thread;

let counter = Arc::new(Mutex::new(0));
let mut handles = vec![];

for _ in 0..5 {
    let counter = Arc::clone(&counter);
    let handle = thread::spawn(move || {
        let mut num = counter.lock().unwrap();
        *num += 1;
    });
    handles.push(handle);
}
for h in handles { h.join().unwrap(); }
println!("Counter: {}", *counter.lock().unwrap());
```

**Key primitives:**

- Arc<T> — atomically reference-counted pointer for sharing across threads.
- Mutex<T> — mutual exclusion guard for interior mutability.
- RwLock<T> — concurrent read / exclusive write guard.

**Channels (mpsc) for communication:**

```rust
use std::sync::mpsc;
use std::thread;

let (tx, rx) = mpsc::channel();
thread::spawn(move || { tx.send(42).unwrap(); });
println!("Got: {}", rx.recv().unwrap());
```

**Send & Sync:**

- `Send` — ownership of the type can be transferred across threads.
- `Sync` — type is safe to reference from multiple threads.
- Standard types (String, Vec) are Send/Sync where safe; closures capturing non-send types will not compile.

**Borrow checker & threads tips:**

- Move ownership to thread via `move` closures or clone into Arc.
- Avoid borrowing local data into a thread without `move` (borrow doesn't outlive scope).
- When using `Arc<Mutex<T>>`, lock only for minimal time to keep concurrency high and avoid deadlocks.

**Example use case:** Safe shared state counters, worker pools, and message passing without data races.

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
