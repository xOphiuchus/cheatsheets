# C++ Design Patterns Cheatsheet (Essential)

---

## Creational Patterns

### Singleton

Ensures only one instance of a class exists and provides global access.

- Use for: Logging, configuration, resource managers.
- Key: Private constructor, static accessor, deleted copy/assignment.

```cpp
class Singleton {
private:
    Singleton() {}
    Singleton(const Singleton&) = delete;
    Singleton& operator=(const Singleton&) = delete;
public:
    static Singleton& getInstance() {
        static Singleton instance;
        return instance;
    }
};
```

---

### Factory Method

Defines an interface for creating objects, lets subclasses decide which class to instantiate.

- Use for: Frameworks, plugin systems, extensible object creation.
- Key: Abstract base with virtual factory method.

```cpp
class Product { /* ... */ };
class Creator {
public:
    virtual Product* factoryMethod() = 0;
};
class ConcreteCreator : public Creator {
public:
    Product* factoryMethod() override { return new Product(); }
};
```

---

## Structural Patterns

### Adapter

Converts one interface to another expected by clients.

- Use for: Integrating legacy code, third-party libraries.
- Key: Implements target interface, holds adaptee.

```cpp
class Target { public: virtual void request() = 0; };
class Adaptee { public: void specificRequest() {} };
class Adapter : public Target {
    Adaptee* adaptee_;
public:
    Adapter(Adaptee* a) : adaptee_(a) {}
    void request() override { adaptee_->specificRequest(); }
};
```

---

### Decorator

Adds responsibilities to objects dynamically.

- Use for: Extending behavior (logging, caching, formatting).
- Key: Wraps component, implements same interface.

```cpp
class Component { public: virtual std::string op() = 0; };
class Decorator : public Component {
    Component* comp_;
public:
    Decorator(Component* c) : comp_(c) {}
    std::string op() override { return comp_->op(); }
};
class LoggingDecorator : public Decorator {
public:
    LoggingDecorator(Component* c) : Decorator(c) {}
    std::string op() override {
        std::cout << "Logging...\n";
        return Decorator::op();
    }
};
```

---

### Proxy

Controls access to another object (real subject).

- Use for: Lazy loading, access control, remote proxies.
- Key: Implements same interface, holds real subject.

```cpp
class Subject { public: virtual void request() = 0; };
class RealSubject : public Subject { public: void request() override {} };
class Proxy : public Subject {
    RealSubject* real_;
public:
    void request() override {
        if (!real_) real_ = new RealSubject();
        real_->request();
    }
};
```

---

### Composite

Treats individual objects and compositions uniformly (tree structure).

- Use for: Hierarchies (files/folders, UI components).
- Key: Component interface, composite holds children.

```cpp
class Component { public: virtual void op() = 0; };
class Leaf : public Component { public: void op() override {} };
class Composite : public Component {
    std::vector<Component*> children_;
public:
    void add(Component* c) { children_.push_back(c); }
    void op() override { for (auto c : children_) c->op(); }
};
```

---

## Behavioral Patterns

### Observer

One-to-many dependency; observers notified on subject change.

- Use for: Event systems, GUIs, data binding.
- Key: Subject holds observer list, notifies on change.

```cpp
class Observer { public: virtual void update() = 0; };
class Subject {
    std::vector<Observer*> observers_;
public:
    void attach(Observer* o) { observers_.push_back(o); }
    void notify() { for (auto o : observers_) o->update(); }
};
```

---

### Strategy

Encapsulates interchangeable algorithms.

- Use for: Sorting, validation, formatting, runtime algorithm selection.
- Key: Strategy interface, context holds strategy.

```cpp
class Strategy { public: virtual int execute(int a, int b) = 0; };
class AddStrategy : public Strategy { public: int execute(int a, int b) override { return a + b; } };
class Context {
    Strategy* strategy_;
public:
    void setStrategy(Strategy* s) { strategy_ = s; }
    int run(int a, int b) { return strategy_->execute(a, b); }
};
```

---

### Template Method

Defines skeleton of an algorithm, lets subclasses implement steps.

- Use for: Workflow steps, build processes, standardized flows.
- Key: Non-virtual template method, virtual primitive steps.

```cpp
class AbstractClass {
public:
    void templateMethod() {
        step1();
        step2();
    }
protected:
    virtual void step1() = 0;
    virtual void step2() = 0;
};
```

---

### Iterator

Provides sequential access to elements without exposing representation.

- Use for: Traversing containers, custom collections.
- Key: Iterator interface, container returns iterator.

```cpp
template <typename T>
class Iterator {
public:
    virtual bool hasNext() = 0;
    virtual T next() = 0;
};
```

---
