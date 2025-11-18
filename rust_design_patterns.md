# 🦀 Rust Design Patterns Cheatsheet (Essential)

---

## Project Essentials

### Cargo & Projects

What it is: Rust's package manager and build system.

Why it's important: Handles building, dependencies, testing, docs.

Basic usage:

```bash
cargo new my_project
cargo build
cargo run
cargo test
```

Key things to remember: Always start with `cargo new`. Use `cargo run` for quick dev cycles.

---

### Cargo.toml & Dependencies

What it is: Manifest file for metadata and dependencies.

Why it's important: Defines project config and external crates.

Basic usage:

```toml
[package]
name = "my_app"
version = "0.1.0"

[dependencies]
rand = "0.8.5"
```

Key things to remember: Add dependencies under `[dependencies]`, then build.

---

### Main Function

What it is: Program entry point.

Why it's important: Where execution begins.

Basic usage:

```rust
fn main() {
    println!("Hello, Rust!");
}
```

Key things to remember: Every binary crate needs `fn main()`.

---

## Creational Patterns

### Singleton

Ensures only one instance exists, provides global access.

- Use for: Config, logging, global state.
- Key: Use `once_cell` and `Mutex` for thread-safe lazy singletons.

```rust
use once_cell::sync::Lazy;
use std::sync::Mutex;
static CONFIG: Lazy<Mutex<AppConfig>> = Lazy::new(|| Mutex::new(AppConfig::load()));
```

---

### Factory Method

Method for creating objects; concrete types decide what to instantiate.

- Use for: Extensible object creation, plugin systems.
- Key: Trait for factory, returns trait objects.

```rust
trait Transport { fn deliver(&self); }
trait Logistics { fn create_transport(&self) -> Box<dyn Transport>; }
struct RoadLogistics;
impl Logistics for RoadLogistics {
    fn create_transport(&self) -> Box<dyn Transport> { Box::new(Truck {}) }
}
```

---

## Structural Patterns

### Adapter

Converts one interface to another.

- Use for: Integrating legacy or third-party code.
- Key: Trait for target interface, struct composition for adaptee.

```rust
trait StandardLogger { fn log(&self, msg: &str); }
struct ExternalLogLibrary;
impl ExternalLogLibrary { fn external_write(&self, data: String) {} }
struct LibraryAdapter { adaptee: ExternalLogLibrary }
impl StandardLogger for LibraryAdapter {
    fn log(&self, msg: &str) { self.adaptee.external_write(msg.to_string()); }
}
```

---

### Decorator

Adds responsibilities to objects dynamically.

- Use for: Logging, caching, formatting.
- Key: Decorator holds trait object, implements same trait.

```rust
trait Coffee { fn cost(&self) -> f64; }
struct MilkDecorator { coffee: Box<dyn Coffee> }
impl Coffee for MilkDecorator {
    fn cost(&self) -> f64 { self.coffee.cost() + 0.50 }
}
```

---

### Proxy

Controls access to another object.

- Use for: Lazy loading, access control, logging.
- Key: Trait for common interface, Option for lazy init.

```rust
trait Image { fn display(&self); }
struct ImageProxy { filename: String, real_image: Option<RealImage> }
impl Image for ImageProxy {
    fn display(&self) {
        // Lazy load real_image if needed
    }
}
```

---

### Composite

Tree structure; treats leaves and composites uniformly.

- Use for: Hierarchies (files/folders, UI).
- Key: Trait objects for heterogeneous collections.

```rust
trait Component { fn print_name(&self); }
struct Folder { name: String, children: Vec<Box<dyn Component>> }
struct File { name: String }
```

---

## Behavioral Patterns

### Observer

One-to-many dependency; observers notified on subject change.

- Use for: Event systems, GUIs, data binding.
- Key: Use Rc/RefCell or Arc/Mutex for shared mutable state.

```rust
trait Observer { fn update(&mut self, data: &str); }
struct Subject { observers: Vec<Box<dyn Observer>> }
```

---

### Strategy

Encapsulates interchangeable algorithms.

- Use for: Sorting, validation, runtime algorithm selection.
- Key: Trait for strategy, trait objects for dynamic dispatch.

```rust
trait SortStrategy { fn sort(&self, data: &mut [i32]); }
struct Sorter { strategy: Box<dyn SortStrategy> }
```

---

### Template Method

Skeleton of algorithm in base trait; steps customized by implementers.

- Use for: Workflow steps, standardized flows.
- Key: Trait for primitive steps, generic function for template.

```rust
trait Builder {
    fn prepare_data(&mut self);
    fn execute_flow(&self);
}
fn run_process<T: Builder>(builder: &mut T) {
    builder.prepare_data();
    println!("Standard step...");
    builder.execute_flow();
}
```

---

### Iterator

Sequential access to elements.

- Use for: Traversing collections, custom containers.
- Key: Implement Iterator or IntoIterator for custom types.

```rust
struct MyCollection { data: Vec<i32> }
impl IntoIterator for MyCollection {
    type Item = i32;
    type IntoIter = std::vec::IntoIter<Self::Item>;
    fn into_iter(self) -> Self::IntoIter { self.data.into_iter() }
}
```

---
