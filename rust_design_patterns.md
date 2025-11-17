# 🦀 Rust Design Patterns Cheatsheet

---

## 🛠️ Rust Project Essentials

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

## 🎭 Behavioral Patterns

### Strategy Pattern

What it is: Encapsulates interchangeable algorithms.

Why it's important: Lets context delegate behavior to chosen strategy.

Basic usage:

```rust
trait SortStrategy { fn sort(&self, data: &mut [i32]); }
struct Sorter { strategy: Box<dyn SortStrategy> }
```

Key things to remember: Use traits for strategy interface, trait objects for dynamic dispatch.

---

### Observer Pattern

What it is: One-to-many dependency; observers notified on subject change.

Why it's important: Decouples data providers and consumers.

Basic usage:

```rust
trait Observer { fn update(&mut self, data: &str); }
struct Subject { observers: Vec<Box<dyn Observer>> }
```

Key things to remember: Use Rc/RefCell or Arc/Mutex for shared mutable state.

---

### Command Pattern

What it is: Encapsulates a request as an object.

Why it's important: Decouples invoker from performer; enables undo/queue.

Basic usage:

```rust
trait Command { fn execute(&mut self); }
// Closure-based command
fn print_command(msg: String) -> Box<dyn FnOnce()> {
    Box::new(move || println!("{}", msg))
}
```

Key things to remember: Closures (`Fn`, `FnMut`, `FnOnce`) are idiomatic for commands.

---

### Template Method Pattern

What it is: Skeleton of algorithm in base trait; steps customized by implementers.

Why it's important: Guarantees structure, allows customization.

Basic usage:

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

Key things to remember: Use traits for primitive steps, generic function for template.

---

### Iterator Pattern

What it is: Sequential access to collection elements.

Why it's important: Standard traversal and processing.

Basic usage:

```rust
struct MyCollection { data: Vec<i32> }
impl IntoIterator for MyCollection {
    type Item = i32;
    type IntoIter = std::vec::IntoIter<Self::Item>;
    fn into_iter(self) -> Self::IntoIter { self.data.into_iter() }
}
```

Key things to remember: Implement `Iterator` or `IntoIterator` for custom types.

---

### State Pattern

What it is: Object alters behavior when internal state changes.

Why it's important: Eliminates complex match/if logic.

Basic usage:

```rust
trait State { fn handle(self: Box<Self>) -> Box<dyn State>; }
struct Context { state: Box<dyn State> }
// Or use enums for simple cases
enum BlogPostState { Draft, Review, Published }
```

Key things to remember: Use trait objects for state transitions; enums for simple state machines.

---

## 🏗️ Structural Patterns

### Decorator Pattern

What it is: Adds responsibilities to objects dynamically.

Why it's important: Flexible alternative to inheritance.

Basic usage:

```rust
trait Coffee { fn cost(&self) -> f64; }
struct MilkDecorator { coffee: Box<dyn Coffee> }
impl Coffee for MilkDecorator {
    fn cost(&self) -> f64 { self.coffee.cost() + 0.50 }
}
```

Key things to remember: Decorator holds trait object and implements same trait.

---

### Adapter Pattern

What it is: Converts one interface to another.

Why it's important: Allows incompatible types to work together.

Basic usage:

```rust
trait StandardLogger { fn log(&self, msg: &str); }
struct ExternalLogLibrary;
impl ExternalLogLibrary { fn external_write(&self, data: String) {} }
struct LibraryAdapter { adaptee: ExternalLogLibrary }
impl StandardLogger for LibraryAdapter {
    fn log(&self, msg: &str) { self.adaptee.external_write(msg.to_string()); }
}
```

Key things to remember: Use traits for target interface, struct composition for adaptee.

---

### Facade Pattern

What it is: Simplifies interface to a complex subsystem.

Why it's important: Hides complexity, coordinates subcomponents.

Basic usage:

```rust
struct SubsystemA; struct SubsystemB;
pub struct CompilerFacade { lexer: SubsystemA, parser: SubsystemB }
impl CompilerFacade {
    pub fn compile(&self, src: &str) {
        // lexer.analyze(src); parser.build_tree(...);
    }
}
```

Key things to remember: Facade struct wraps subsystems, exposes high-level methods.

---

### Composite Pattern

What it is: Tree structure; treats leaves and composites uniformly.

Why it's important: Simplifies recursion and uniform handling.

Basic usage:

```rust
trait Component { fn print_name(&self); }
struct Folder { name: String, children: Vec<Box<dyn Component>> }
struct File { name: String }
```

Key things to remember: Use trait objects for heterogeneous collections.

---

### Proxy Pattern

What it is: Surrogate for another object to control access.

Why it's important: Enables lazy loading, access control, logging.

Basic usage:

```rust
trait Image { fn display(&self); }
struct ImageProxy { filename: String, real_image: Option<RealImage> }
impl Image for ImageProxy {
    fn display(&self) {
        // Lazy load real_image if needed
    }
}
```

Key things to remember: Use Option for lazy init; trait for common interface.

---

## 🏗️ Creational Patterns

### Factory Method Pattern

What it is: Method for creating objects; concrete types decide what to instantiate.

Why it's important: Decouples client from concrete types.

Basic usage:

```rust
trait Transport { fn deliver(&self); }
trait Logistics { fn create_transport(&self) -> Box<dyn Transport>; }
struct RoadLogistics;
impl Logistics for RoadLogistics {
    fn create_transport(&self) -> Box<dyn Transport> { Box::new(Truck {}) }
}
```

Key things to remember: Factory trait returns trait objects.

---

### Abstract Factory Pattern

What it is: Interface for creating families of related objects.

Why it's important: Ensures compatibility among products.

Basic usage:

```rust
trait Button { fn render(&self); }
trait Checkbox { fn render(&self); }
trait GUIFactory {
    fn create_button(&self) -> Box<dyn Button>;
    fn create_checkbox(&self) -> Box<dyn Checkbox>;
}
struct MacFactory; // implements GUIFactory
```

Key things to remember: Factory trait returns multiple product trait objects.

---

### Singleton Pattern

What it is: Ensures only one instance exists, provides global access.

Why it's important: Used rarely in Rust; must be thread-safe.

Basic usage:

```rust
use once_cell::sync::Lazy;
use std::sync::Mutex;

static CONFIG: Lazy<Mutex<AppConfig>> = Lazy::new(|| Mutex::new(AppConfig::load()));
// Access: let mut config = CONFIG.lock().unwrap();
```

Key things to remember: Use `once_cell` and `Mutex` for thread-safe lazy singletons.

---
