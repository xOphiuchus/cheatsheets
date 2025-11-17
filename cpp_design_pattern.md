# C++ Design Patterns Cheatsheet

---

## 🏗️ Creational Patterns

### Builder Pattern

What it is: Separates the construction of a complex object from its representation, allowing the same construction process to create different results.

Why it's important: Gives finer control over object creation and avoids the "Telescoping Constructor" anti-pattern.

Basic syntax and usage:

```cpp
class Product { /* ... parts ... */ };

class Builder {
public:
    virtual void buildPartA() = 0;
    virtual void buildPartB() = 0;
    virtual Product* getResult() = 0;
};

class Director { // Optional, orchestrates the build
public:
    void construct(Builder* builder) {
        builder->buildPartA();
        builder->buildPartB();
    }
};
```

Key things to remember: A separate `Director` is optional; `getResult()` retrieves the constructed object.

Example Use Case: Building complex documents (HTML, PDF) where structure is constant but content varies.

---

### Factory Method Pattern

What it is: Defines an interface for creating an object, but lets subclasses alter the type of objects that will be created.

Why it's important: Promotes loose coupling by delegating instantiation logic to subclasses.

Basic syntax and usage:

```cpp
class Product { /* ... */ };
class ConcreteProductA : public Product { /* ... */ };

class Creator {
public:
    virtual Product* factoryMethod() = 0;
    void someOperation() {
        Product* product = factoryMethod();
        // ...
    }
};

class ConcreteCreatorA : public Creator {
public:
    Product* factoryMethod() override {
        return new ConcreteProductA();
    }
};
```

Key things to remember: Creation via inheritance and overriding. Client code uses Creator interface only.

Example Use Case: Logger framework where base class handles logic and subclasses produce file/db loggers.

---

### Abstract Factory Pattern

What it is: Provides an interface for creating families of related or dependent objects without specifying their concrete classes.

Why it's important: Ensures product consistency by producing objects from the same family.

Basic syntax and usage:

```cpp
class AbstractProductA { /* ... */ };
class AbstractProductB { /* ... */ };

class AbstractFactory {
public:
    virtual AbstractProductA* createProductA() = 0;
    virtual AbstractProductB* createProductB() = 0;
};

class ConcreteFactory1 : public AbstractFactory {
public:
    AbstractProductA* createProductA() override { /* ... */ }
    AbstractProductB* createProductB() override { /* ... */ }
};
```

Key things to remember: Creates sets of objects. Useful for selecting a configuration group (OS-specific widgets).

Example Use Case: Cross-platform GUI factories producing matching widgets for Windows/Mac/Linux.

---

### Prototype Pattern

What it is: Creates new objects by cloning an existing object (the prototype) instead of using constructors.

Why it's important: Avoids coupling to concrete classes and helps when instantiation is costly or complex.

Basic syntax and usage:

```cpp
class IPrototype {
public:
    virtual IPrototype* clone() = 0;
    virtual ~IPrototype() = default;
};

class ConcretePrototype : public IPrototype {
public:
    IPrototype* clone() override {
        return new ConcretePrototype(*this); // copy constructor
    }
};
```

Key things to remember: `clone()` delegates to copy constructor; manage deep vs. shallow copies properly.

Example Use Case: Cloning pre-configured game entities or templates.

---

### Singleton Pattern

What it is: Ensures a class has only one instance and provides a global access point.

Why it's important: Controls access to shared resources and prevents multiple interfering instances.

Basic syntax and usage:

```cpp
class Singleton {
private:
    Singleton() {}
    Singleton(const Singleton&) = delete;
    Singleton& operator=(const Singleton&) = delete;
public:
    static Singleton& getInstance() {
        static Singleton instance; // thread-safe since C++11
        return instance;
    }
    void log(const std::string& msg) { /* ... */ }
};
```

Key things to remember: Delete copy/assignment; use function-local static for lazy, thread-safe init in C++11+.

Example Use Case: Global logger or configuration manager.

---

## 🏗️ Structural Patterns

### Adapter Pattern

What it is: Converts the interface of an existing class into another interface clients expect.

Why it's important: Allows incompatible classes to work together via a wrapper.

Basic syntax and usage:

```cpp
class Target {
public:
    virtual void request() = 0;
};

class Adaptee {
public:
    void specificRequest() { /* ... */ }
};

class Adapter : public Target {
private:
    Adaptee* adaptee_;
public:
    Adapter(Adaptee* a) : adaptee_(a) {}
    void request() override { adaptee_->specificRequest(); }
};
```

Key things to remember: Adapter implements desired interface and delegates to Adaptee (object or class adapter).

Example Use Case: Wrap a modern library to match an old engine's API.

---

### Bridge Pattern

What it is: Decouples an abstraction from its implementation so both can vary independently.

Why it's important: Avoids combinatorial explosion when two dimensions vary.

Basic syntax and usage:

```cpp
class Implementation {
public:
    virtual void operationImpl() = 0;
};

class Abstraction {
protected:
    Implementation* impl_;
public:
    Abstraction(Implementation* i) : impl_(i) {}
    virtual void operation() { impl_->operationImpl(); }
};

class ConcreteAbstraction : public Abstraction { /* ... */ };
```

Key things to remember: Two parallel hierarchies; Abstraction holds reference to Implementation.

Example Use Case: Shapes (Circle/Square) vs rendering APIs (OpenGL/DirectX).

---

### Composite Pattern

What it is: Composes objects into tree structures to represent part–whole hierarchies.

Why it's important: Treats individual objects and compositions uniformly.

Basic syntax and usage:

```cpp
class Component {
public:
    virtual void operation() = 0;
    virtual void add(Component*) {}
};

class Leaf : public Component {
public:
    void operation() override { /* ... */ }
};

class Composite : public Component {
private:
    std::vector<Component*> children_;
public:
    void add(Component* c) override { children_.push_back(c); }
    void operation() override {
        for (auto c : children_) c->operation();
    }
};
```

Key things to remember: Composite holds Component pointers; recursion handles operations.

Example Use Case: File system: files (leaf) and folders (composite).

---

### Decorator Pattern

What it is: Adds responsibilities to objects dynamically by wrapping them.

Why it's important: Flexible alternative to subclassing for extended behavior.

Basic syntax and usage:

```cpp
class Component {
public:
    virtual std::string operation() = 0;
};

class Decorator : public Component {
protected:
    Component* component_;
public:
    Decorator(Component* c) : component_(c) {}
    std::string operation() override { return component_->operation(); }
};

class ConcreteDecoratorA : public Decorator {
public:
    ConcreteDecoratorA(Component* c) : Decorator(c) {}
    std::string operation() override {
        return "A(" + Decorator::operation() + ")";
    }
};
```

Key things to remember: Decorators wrap components; can be stacked.

Example Use Case: Adding scrollbars, borders, or compression/encryption to streams.

---

### Facade Pattern

What it is: Provides a simplified interface to a complex subsystem.

Why it's important: Hides subsystem complexity and makes usage simpler.

Basic syntax and usage:

```cpp
class SubsystemA { public: void method1() {} };
class SubsystemB { public: void method2() {} };

class Facade {
private:
    SubsystemA* a_;
    SubsystemB* b_;
public:
    Facade() { a_ = new SubsystemA(); b_ = new SubsystemB(); }
    void simplifyOperation() {
        a_->method1();
        b_->method2();
    }
};
```

Key things to remember: Facade simplifies use; it does not add new functionality.

Example Use Case: HomeTheater.watchMovie() that coordinates projector, lights, and player.

---

### Flyweight Pattern

What it is: Shares intrinsic state among many objects to reduce memory use.

Why it's important: Saves memory when many similar objects exist.

Basic syntax and usage:

```cpp
class Flyweight {
private:
    const std::string sharedState_;
public:
    Flyweight(const std::string& s) : sharedState_(s) {}
    void operation(const std::string& uniqueState) { /* ... */ }
};

class FlyweightFactory {
private:
    std::map<std::string, Flyweight*> cache_;
public:
    Flyweight* getFlyweight(const std::string& key) {
        if (cache_.find(key) == cache_.end()) cache_[key] = new Flyweight(key);
        return cache_[key];
    }
};
```

Key things to remember: Separate intrinsic (shared) and extrinsic (unique) state; factory manages shared instances.

Example Use Case: Rendering thousands of similar objects (trees, characters).

---

### Proxy Pattern

What it is: Provides a surrogate for another object to control access.

Why it's important: Useful for lazy loading, access control, and logging.

Basic syntax and usage:

```cpp
class Subject { public: virtual void request() = 0; };

class RealSubject : public Subject {
public:
    void request() override { /* heavy operation */ }
};

class Proxy : public Subject {
private:
    RealSubject* realSubject_ = nullptr;
public:
    void request() override {
        if (!realSubject_) realSubject_ = new RealSubject(); // lazy
        realSubject_->request();
    }
};
```

Key things to remember: Proxy implements same interface as RealSubject; can add pre/post processing.

Example Use Case: Lazy-loading large resources or access-controlled resources.

---

## 🎭 Behavioral Patterns

### Chain of Responsibility Pattern

What it is: Passes a request along a chain of handlers until one handles it.

Why it's important: Decouples sender and receiver; handlers can be added/removed dynamically.

Basic syntax and usage:

```cpp
class Handler {
protected:
    Handler* nextHandler_;
public:
    void setNext(Handler* handler) { nextHandler_ = handler; }
    virtual void handleRequest(int level) = 0;
};

class ConcreteHandler : public Handler {
public:
    void handleRequest(int level) override {
        if (level < 5) { /* handle */ }
        else if (nextHandler_) nextHandler_->handleRequest(level);
    }
};
```

Key things to remember: End of chain may leave requests unhandled.

Example Use Case: Escalation chain for approvals/requests.

---

### Command Pattern

What it is: Encapsulates a request as an object so you can parameterize clients, queue requests, and support undo.

Why it's important: Enables undo/redo, logging, and queuing.

Basic syntax and usage:

```cpp
class Receiver { public: void action() {} };

class Command {
public:
    virtual void execute() = 0;
    virtual void undo() = 0;
};

class ConcreteCommand : public Command {
private:
    Receiver* receiver_;
public:
    ConcreteCommand(Receiver* r) : receiver_(r) {}
    void execute() override { receiver_->action(); }
    void undo() override { /* reverse */ }
};
```

Key things to remember: Command decouples invoker from receiver.

Example Use Case: Undo/redo in editors and transactional operations.

---

### Interpreter Pattern

What it is: Implements a simple language's grammar and interpreter.

Why it's important: Good for small domain-specific languages and rule engines.

Basic syntax and usage:

```cpp
class Context { /* ... */ };

class AbstractExpression {
public:
    virtual void interpret(Context* context) = 0;
};
```

Key things to remember: Best for simple DSLs, not full general-purpose languages.

Example Use Case: Simple query or expression evaluators.

---

### Iterator Pattern

What it is: Provides sequential access to aggregate elements without exposing internal representation.

Why it's important: Decouples traversal from collection; supports multiple traversal strategies.

Basic syntax and usage:

```cpp
template <typename T>
class Iterator {
public:
    virtual bool hasNext() = 0;
    virtual T next() = 0;
};
```

Key things to remember: C++ std::iterators are the standard example; range-based for uses them.

Example Use Case: Custom iterators for trees or graphs.

---

### Mediator Pattern

What it is: Centralizes communication between related objects (colleagues) in a mediator.

Why it's important: Reduces complex interconnections and coupling.

Basic syntax and usage:

```cpp
class Colleague;
class Mediator { public: virtual void notify(Colleague*, const std::string&) = 0; };

class Colleague {
protected:
    Mediator* mediator_;
public:
    Colleague(Mediator* m) : mediator_(m) {}
};
```

Key things to remember: Communication flows through mediator; simplifies relationships.

Example Use Case: Chat room coordinator or UI component orchestrator.

---

### Memento Pattern

What it is: Captures and externalizes an object's internal state so it can be restored later.

Why it's important: Provides undo/rollback without violating encapsulation.

Basic syntax and usage:

```cpp
class Memento {
private:
    friend class Originator;
    std::string state_;
public:
    Memento(const std::string& s) : state_(s) {}
};

class Originator {
private:
    std::string state_;
public:
    Memento* save() { return new Memento(state_); }
    void restore(Memento* m) { state_ = m->state_; }
};
```

Key things to remember: Caretaker stores mementos but cannot inspect them.

Example Use Case: Multi-level undo in editors.

---

### Observer Pattern

What it is: Defines a one-to-many dependency so observers are notified when subject changes.

Why it's important: Decouples subject from observers; foundation of event-driven systems.

Basic syntax and usage:

```cpp
class Observer { public: virtual void update(const std::string& state) = 0; };

class Subject {
private:
    std::vector<Observer*> observers_;
public:
    void attach(Observer* o) { observers_.push_back(o); }
    void notifyObservers(const std::string& state) {
        for (auto o : observers_) o->update(state);
    }
};
```

Key things to remember: Inversion of Control — Subject notifies observers.

Example Use Case: UI update subscriptions, stock tickers notifying displays.

---

### State Pattern

What it is: Allows an object to change behavior when internal state changes by delegating to state objects.

Why it's important: Replaces complex conditional logic with state classes.

Basic syntax and usage:

```cpp
class Context;
class State { public: virtual void handle(Context* context) = 0; };

class ConcreteStateA : public State {
public:
    void handle(Context* context) override {
        // context->setState(new ConcreteStateB());
    }
};

class Context {
private:
    State* state_;
public:
    void request() { state_->handle(this); }
    void setState(State* s) { state_ = s; }
};
```

Key things to remember: Each state encapsulates its own behavior; context delegates to current state.

Example Use Case: Network connection states (Disconnected/Connecting/Connected).

---

### Strategy Pattern

What it is: Encapsulates interchangeable algorithms and makes them selectable at runtime.

Why it's important: Enables selecting algorithms independently of clients.

Basic syntax and usage:

```cpp
class Strategy { public: virtual int execute(int a, int b) = 0; };

class ConcreteStrategyAdd : public Strategy {
public:
    int execute(int a, int b) override { return a + b; }
};

class Context {
private:
    Strategy* strategy_;
public:
    void setStrategy(Strategy* s) { strategy_ = s; }
    int executeStrategy(int a, int b) { return strategy_->execute(a, b); }
};
```

Key things to remember: Strategy encapsulates algorithm; Context uses it.

Example Use Case: Swappable sorting or validation algorithms.

---

### Template Method Pattern

What it is: Defines skeleton of an algorithm in a base class and lets subclasses implement steps.

Why it's important: Enforces algorithm structure while allowing customization of steps.

Basic syntax and usage:

```cpp
class AbstractClass {
public:
    void templateMethod() {
        step1();
        step2();
        hook();
    }
protected:
    void step1() { /* concrete */ }
    virtual void step2() = 0;
    virtual void hook() {}
};

class ConcreteClass : public AbstractClass {
protected:
    void step2() override { /* ... */ }
};
```

Key things to remember: Use non-virtual templateMethod to fix algorithm flow.

Example Use Case: Build process where steps are fixed but implementations vary.

---

### Visitor Pattern

What it is: Lets you define new operations on object structures without changing the classes of the elements.

Why it's important: Adds operations while keeping element classes unchanged (double dispatch).

Basic syntax and usage:

```cpp
class Visitor;
class Element { public: virtual void accept(Visitor* v) = 0; };

class ConcreteElementA : public Element {
public:
    void accept(Visitor* v) override; // implemented below
};

class Visitor {
public:
    virtual void visitConcreteElementA(ConcreteElementA* e) = 0;
    // other visit methods...
};

void ConcreteElementA::accept(Visitor* visitor) {
    visitor->visitConcreteElementA(this);
}
```

Key things to remember: Requires double dispatch; adding new elements requires updating all visitors.

Example Use Case: Performing operations (e.g., printing, calculating) over a composite object structure without modifying element classes.

---
