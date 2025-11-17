# Java Design Patterns Cheatsheet

---

## 🏗️ Creational Patterns

### Builder Pattern

What it is: Separates construction of a complex object from its representation.

Why it's important: Avoids telescoping constructors and gives fine control over object creation.

Basic syntax and usage:

```java
class Product {
    private String partA, partB;
    private Product(Builder builder) {
        this.partA = builder.partA;
        this.partB = builder.partB;
    }
    public static class Builder {
        private String partA, partB;
        public Builder buildPartA(String a) { this.partA = a; return this; }
        public Builder buildPartB(String b) { this.partB = b; return this; }
        public Product build() { return new Product(this); }
    }
}
// Usage: Product p = new Product.Builder().buildPartA("X").buildPartB("Y").build();
```

Key things to remember: Builder is usually a static inner class; method chaining is common.

Example Use Case: Building complex objects like AlertDialog or HTTP requests.

---

### Factory Method Pattern

What it is: Defines an interface for creating an object, lets subclasses decide which class to instantiate.

Why it's important: Promotes loose coupling by deferring instantiation to subclasses.

Basic syntax and usage:

```java
interface Product {}
class ConcreteProductA implements Product {}

abstract class Creator {
    public abstract Product factoryMethod();
    public void someOperation() {
        Product product = factoryMethod();
        // ...
    }
}
class ConcreteCreatorA extends Creator {
    public Product factoryMethod() { return new ConcreteProductA(); }
}
```

Key things to remember: Creation via inheritance and overriding.

Example Use Case: Document editor with createDocument() overridden for each document type.

---

### Abstract Factory Pattern

What it is: Interface for creating families of related objects without specifying concrete classes.

Why it's important: Ensures product consistency for a family of objects.

Basic syntax and usage:

```java
interface AbstractProductA {}
interface AbstractProductB {}
interface AbstractFactory {
    AbstractProductA createProductA();
    AbstractProductB createProductB();
}
class ConcreteFactory1 implements AbstractFactory {
    public AbstractProductA createProductA() { return new ConcreteProductA1(); }
    public AbstractProductB createProductB() { return new ConcreteProductB1(); }
}
```

Key things to remember: Used for configuration groups (UI toolkit, DB vendor).

Example Use Case: UI toolkit producing matching widgets for Mac/Windows.

---

### Prototype Pattern

What it is: Creates new objects by cloning an existing object.

Why it's important: Useful when object creation is expensive or complex.

Basic syntax and usage:

```java
class ConcretePrototype implements Cloneable {
    public Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}
// Usage: ConcretePrototype p2 = (ConcretePrototype) p1.clone();
```

Key things to remember: Implement Cloneable; handle deep copy logic if needed.

Example Use Case: Cloning game objects or database connections.

---

### Singleton Pattern

What it is: Ensures a class has only one instance and provides global access.

Why it's important: Controls access to shared resources.

Basic syntax and usage:

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

Key things to remember: Use private constructor and static accessor; consider enum or inner class for thread safety.

Example Use Case: Logger, configuration manager, thread pool.

---

## 🏗️ Structural Patterns

### Adapter Pattern

What it is: Converts the interface of a class into another interface clients expect.

Why it's important: Allows incompatible classes to work together.

Basic syntax and usage:

```java
interface Target { void request(); }
class Adaptee { public void specificRequest() {} }
class Adapter implements Target {
    private Adaptee adaptee;
    public Adapter(Adaptee a) { adaptee = a; }
    public void request() { adaptee.specificRequest(); }
}
```

Key things to remember: Prefer object adapter (composition) in Java.

Example Use Case: Wrapping XML library to provide JSON interface.

---

### Bridge Pattern

What it is: Decouples abstraction from implementation so both can vary independently.

Why it's important: Avoids class explosion when two dimensions vary.

Basic syntax and usage:

```java
interface Implementation { void operationImpl(); }
abstract class Abstraction {
    protected Implementation impl;
    public Abstraction(Implementation i) { impl = i; }
    public void operation() { impl.operationImpl(); }
}
class ConcreteAbstraction extends Abstraction { /* ... */ }
```

Key things to remember: Two parallel hierarchies; abstraction holds reference to implementation.

Example Use Case: Message types vs sending mechanisms.

---

### Composite Pattern

What it is: Composes objects into tree structures for part-whole hierarchies.

Why it's important: Treats individual and composite objects uniformly.

Basic syntax and usage:

```java
interface Component { void operation(); }
class Leaf implements Component { public void operation() {} }
class Composite implements Component {
    private List<Component> children = new ArrayList<>();
    public void add(Component c) { children.add(c); }
    public void operation() { for (Component c : children) c.operation(); }
}
```

Key things to remember: Composite holds Component references; recursion for operations.

Example Use Case: GUI elements or organization charts.

---

### Decorator Pattern

What it is: Adds responsibilities to objects dynamically by wrapping them.

Why it's important: Flexible alternative to subclassing for extended behavior.

Basic syntax and usage:

```java
interface Component { String operation(); }
abstract class Decorator implements Component {
    protected Component component;
    public Decorator(Component c) { component = c; }
    public String operation() { return component.operation(); }
}
class ConcreteDecoratorA extends Decorator {
    public ConcreteDecoratorA(Component c) { super(c); }
    public String operation() { return "A(" + super.operation() + ")"; }
}
```

Key things to remember: Decorators wrap components; can be stacked.

Example Use Case: Java I/O streams, coffee with milk/sugar decorators.

---

### Facade Pattern

What it is: Provides a simplified interface to a complex subsystem.

Why it's important: Hides subsystem complexity.

Basic syntax and usage:

```java
class SubsystemA { public void method1() {} }
class SubsystemB { public void method2() {} }
class Facade {
    private SubsystemA a = new SubsystemA();
    private SubsystemB b = new SubsystemB();
    public void simplifyOperation() { a.method1(); b.method2(); }
}
```

Key things to remember: Facade simplifies use; does not add new features.

Example Use Case: Compiler interface coordinating lexer, parser, codegen.

---

### Flyweight Pattern

What it is: Shares intrinsic state among many objects to reduce memory use.

Why it's important: Saves memory for large numbers of similar objects.

Basic syntax and usage:

```java
class Flyweight {
    private final String sharedState;
    public Flyweight(String s) { sharedState = s; }
    public void operation(String uniqueState) { /* ... */ }
}
class FlyweightFactory {
    private static final Map<String, Flyweight> cache = new HashMap<>();
    public static Flyweight getFlyweight(String key) {
        if (!cache.containsKey(key)) cache.put(key, new Flyweight(key));
        return cache.get(key);
    }
}
```

Key things to remember: Factory manages shared instances; use when many identical objects.

Example Use Case: String pool, graphical objects.

---

### Proxy Pattern

What it is: Provides a surrogate for another object to control access.

Why it's important: Useful for lazy loading, access control, logging.

Basic syntax and usage:

```java
interface Subject { void request(); }
class RealSubject implements Subject { public void request() {} }
class Proxy implements Subject {
    private RealSubject realSubject;
    public void request() {
        if (realSubject == null) realSubject = new RealSubject();
        realSubject.request();
    }
}
```

Key things to remember: Proxy implements same interface as RealSubject.

Example Use Case: Remote proxy, protection proxy, virtual proxy.

---

## 🎭 Behavioral Patterns

### Chain of Responsibility Pattern

What it is: Passes a request along a chain of handlers until one handles it.

Why it's important: Decouples sender and receiver; handlers can be added/removed dynamically.

Basic syntax and usage:

```java
abstract class Handler {
    protected Handler nextHandler;
    public void setNext(Handler handler) { nextHandler = handler; }
    public abstract void handleRequest(int level);
}
class ConcreteHandler extends Handler {
    public void handleRequest(int level) {
        if (level < 5) { /* handle */ }
        else if (nextHandler != null) nextHandler.handleRequest(level);
    }
}
```

Key things to remember: End of chain may leave requests unhandled.

Example Use Case: Logging, approval chains.

---

### Command Pattern

What it is: Encapsulates a request as an object so you can parameterize clients, queue requests, and support undo.

Why it's important: Enables undo/redo, logging, and queuing.

Basic syntax and usage:

```java
interface Command { void execute(); }
class Receiver { public void action() {} }
class ConcreteCommand implements Command {
    private Receiver receiver;
    public ConcreteCommand(Receiver r) { receiver = r; }
    public void execute() { receiver.action(); }
}
```

Key things to remember: Command decouples invoker from receiver.

Example Use Case: Remote control buttons, undo/redo in editors.

---

### Interpreter Pattern

What it is: Implements a simple language's grammar and interpreter.

Why it's important: Good for small domain-specific languages and rule engines.

Basic syntax and usage:

```java
class Context { /* ... */ }
interface Expression { int interpret(Context context); }
class TerminalExpression implements Expression {
    private final int value;
    public TerminalExpression(int val) { value = val; }
    public int interpret(Context context) { return value; }
}
class NonTerminalExpression implements Expression {
    private Expression left, right;
    public int interpret(Context context) { return left.interpret(context) + right.interpret(context); }
}
```

Key things to remember: Best for simple DSLs, not full general-purpose languages.

Example Use Case: Arithmetic expression evaluators, rule engines.

---

### Iterator Pattern

What it is: Provides sequential access to aggregate elements without exposing internal representation.

Why it's important: Decouples traversal from collection; supports multiple traversal strategies.

Basic syntax and usage:

```java
import java.util.Iterator;
import java.util.List;
class ConcreteAggregate {
    private List<String> items;
    public Iterator<String> createIterator() { return items.iterator(); }
}
// Usage: for (String item : list) { ... }
```

Key things to remember: Java's Iterator and Iterable are standard; enhanced for loop uses them.

Example Use Case: Traversal of collections, custom iterators for trees.

---

### Mediator Pattern

What it is: Centralizes communication between related objects (colleagues) in a mediator.

Why it's important: Reduces complex interconnections and coupling.

Basic syntax and usage:

```java
abstract class Colleague {
    protected Mediator mediator;
    public Colleague(Mediator m) { mediator = m; }
}
interface Mediator { void notify(Colleague sender, String event); }
class ConcreteMediator implements Mediator {
    private ConcreteColleagueA colA;
    private ConcreteColleagueB colB;
    public void setColleagues(ConcreteColleagueA a, ConcreteColleagueB b) { /* ... */ }
    public void notify(Colleague sender, String event) {
        if (sender == colA && event.equals("sent")) colB.receive();
    }
}
```

Key things to remember: Communication flows through mediator; simplifies relationships.

Example Use Case: Air traffic control, chat room coordinator.

---

### Memento Pattern

What it is: Captures and externalizes an object's internal state so it can be restored later.

Why it's important: Provides undo/rollback without violating encapsulation.

Basic syntax and usage:

```java
class Memento {
    private final String state;
    private Memento(String state) { this.state = state; }
}
class Originator {
    private String state;
    Memento save() { return new Memento(state); }
    void restore(Memento m) { state = m.state; }
}
```

Key things to remember: Caretaker stores mementos but cannot inspect them.

Example Use Case: Undo/redo in editors, game save states.

---

### Observer Pattern

What it is: Defines a one-to-many dependency so observers are notified when subject changes.

Why it's important: Decouples subject from observers; foundation of event-driven systems.

Basic syntax and usage:

```java
interface Observer { void update(String state); }
class Subject {
    private List<Observer> observers = new ArrayList<>();
    public void attach(Observer o) { observers.add(o); }
    public void notifyObservers(String state) { for (Observer o : observers) o.update(state); }
}
```

Key things to remember: Subject notifies observers via update().

Example Use Case: UI event listeners, publish/subscribe systems.

---

### State Pattern

What it is: Allows an object to change behavior when internal state changes by delegating to state objects.

Why it's important: Replaces complex conditional logic with state classes.

Basic syntax and usage:

```java
interface State { void handle(Context context); }
class ConcreteStateA implements State {
    public void handle(Context context) { /* context.setState(new ConcreteStateB()); */ }
}
class Context {
    private State state;
    public void request() { state.handle(this); }
    public void setState(State s) { state = s; }
}
```

Key things to remember: Each state encapsulates its own behavior; context delegates to current state.

Example Use Case: ATM states, workflow steps.

---

### Strategy Pattern

What it is: Encapsulates interchangeable algorithms and makes them selectable at runtime.

Why it's important: Enables selecting algorithms independently of clients.

Basic syntax and usage:

```java
interface Strategy { int execute(int a, int b); }
class ConcreteStrategyAdd implements Strategy { public int execute(int a, int b) { return a + b; } }
class Context {
    private Strategy strategy;
    public Context(Strategy s) { strategy = s; }
    public int executeStrategy(int a, int b) { return strategy.execute(a, b); }
}
```

Key things to remember: Strategy encapsulates algorithm; Context uses it.

Example Use Case: Payment methods, sorting algorithms.

---

### Template Method Pattern

What it is: Defines skeleton of an algorithm in a base class and lets subclasses implement steps.

Why it's important: Enforces algorithm structure while allowing customization of steps.

Basic syntax and usage:

```java
abstract class AbstractClass {
    public final void templateMethod() {
        step1();
        step2();
        hook();
    }
    protected abstract void step2();
    protected void hook() {}
    private void step1() { /* ... */ }
}
class ConcreteClass extends AbstractClass {
    protected void step2() { /* ... */ }
}
```

Key things to remember: Use final templateMethod to fix algorithm flow.

Example Use Case: Online transaction steps, build process.

---

### Visitor Pattern

What it is: Lets you define new operations on object structures without changing the classes of the elements.

Why it's important: Adds operations while keeping element classes unchanged (double dispatch).

Basic syntax and usage:

```java
interface Element { void accept(Visitor visitor); }
class ConcreteElementA implements Element {
    public void accept(Visitor visitor) { visitor.visit(this); }
}
interface Visitor {
    void visit(ConcreteElementA element);
    void visit(ConcreteElementB element);
}
class SalaryVisitor implements Visitor {
    public void visit(ConcreteElementA element) { /* ... */ }
    public void visit(ConcreteElementB element) { /* ... */ }
}
```

Key things to remember: Requires double dispatch; adding new elements requires updating all visitors.

Example Use Case: Output formats (JSON/XML) for document models.

---
