# Java Design Patterns Cheatsheet (Essential)

---

## Creational Patterns

### Singleton

Ensures only one instance exists, provides global access.

- Use for: Logging, config, resource managers.
- Key: Private constructor, static accessor, thread safety.

```java
public class Singleton {
    private static Singleton instance;
    private Singleton() {}
    public static synchronized Singleton getInstance() {
        if (instance == null) instance = new Singleton();
        return instance;
    }
}
```

---

### Factory Method

Interface for creating objects, subclasses decide which to instantiate.

- Use for: Frameworks, extensible object creation.
- Key: Abstract base, overridden factory method.

```java
interface Product {}
abstract class Creator {
    public abstract Product factoryMethod();
}
class ConcreteCreator extends Creator {
    public Product factoryMethod() { return new ConcreteProduct(); }
}
```

---

## Structural Patterns

### Adapter

Converts one interface to another.

- Use for: Integrating legacy or third-party code.
- Key: Implements target interface, holds adaptee.

```java
interface Target { void request(); }
class Adaptee { void specificRequest() {} }
class Adapter implements Target {
    private Adaptee adaptee;
    public Adapter(Adaptee a) { adaptee = a; }
    public void request() { adaptee.specificRequest(); }
}
```

---

### Decorator

Adds responsibilities to objects dynamically.

- Use for: Logging, caching, formatting.
- Key: Wraps component, implements same interface.

```java
interface Component { String op(); }
abstract class Decorator implements Component {
    protected Component comp;
    public Decorator(Component c) { comp = c; }
    public String op() { return comp.op(); }
}
class LoggingDecorator extends Decorator {
    public LoggingDecorator(Component c) { super(c); }
    public String op() { System.out.println("Logging"); return super.op(); }
}
```

---

### Proxy

Controls access to another object.

- Use for: Lazy loading, access control, remote proxies.
- Key: Implements same interface, holds real subject.

```java
interface Subject { void request(); }
class RealSubject implements Subject { public void request() {} }
class Proxy implements Subject {
    private RealSubject real;
    public void request() {
        if (real == null) real = new RealSubject();
        real.request();
    }
}
```

---

### Composite

Tree structure; treats leaves and composites uniformly.

- Use for: Hierarchies (files/folders, UI).
- Key: Component interface, composite holds children.

```java
interface Component { void op(); }
class Leaf implements Component { public void op() {} }
class Composite implements Component {
    private List<Component> children = new ArrayList<>();
    public void add(Component c) { children.add(c); }
    public void op() { for (Component c : children) c.op(); }
}
```

---

## Behavioral Patterns

### Observer

One-to-many dependency; observers notified on subject change.

- Use for: Event systems, GUIs, data binding.
- Key: Subject holds observer list, notifies on change.

```java
interface Observer { void update(); }
class Subject {
    private List<Observer> observers = new ArrayList<>();
    public void attach(Observer o) { observers.add(o); }
    public void notifyObservers() { for (Observer o : observers) o.update(); }
}
```

---

### Strategy

Encapsulates interchangeable algorithms.

- Use for: Sorting, validation, runtime algorithm selection.
- Key: Strategy interface, context holds strategy.

```java
interface Strategy { int execute(int a, int b); }
class AddStrategy implements Strategy { public int execute(int a, int b) { return a + b; } }
class Context {
    private Strategy strategy;
    public void setStrategy(Strategy s) { strategy = s; }
    public int run(int a, int b) { return strategy.execute(a, b); }
}
```

---

### Template Method

Defines skeleton of algorithm, lets subclasses implement steps.

- Use for: Workflow steps, standardized flows.
- Key: Final template method, abstract primitive steps.

```java
abstract class AbstractClass {
    public final void templateMethod() {
        step1();
        step2();
    }
    protected abstract void step1();
    protected abstract void step2();
}
```

---

### Iterator

Sequential access to elements without exposing representation.

- Use for: Traversing collections, custom containers.
- Key: Iterator interface, container returns iterator.

```java
interface Iterator<T> {
    boolean hasNext();
    T next();
}
```

---
