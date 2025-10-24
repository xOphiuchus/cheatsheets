# TypeScript Cheatsheet

---

## What is TypeScript?

- Superset of JS, adds static types.
- Compiles to JS with `tsc`.
- Type annotations:
  ```typescript
  let name: string = "Alice";
  function add(a: number, b: number): number {
    return a + b;
  }
  ```

---

## Setup & Compile

- Install: `npm install -g typescript`
- Init config: `tsc --init`
- Compile: `tsc`
- Key `tsconfig.json` options:
  - `"target": "es2020"`
  - `"strict": true`
  - `"sourceMap": true` (for debugging)

---

## Built-In Types

- Primitives: `string`, `number`, `boolean`
- Arrays: `number[]` or `Array<number>`
- Any: `any` (avoid if possible)
- Void: for functions that return nothing

---

## Type Annotations

- Variables:
  ```typescript
  let age: number = 30;
  ```
- Functions:
  ```typescript
  function greet(name: string): void { ... }
  ```

---

## Tuples

- Fixed-length, typed arrays:
  ```typescript
  let point: [number, number] = [1, 2];
  ```

---

## Enums

- Named constants:
  ```typescript
  enum Direction {
    Up,
    Down,
    Left,
    Right,
  }
  let dir: Direction = Direction.Up;
  ```

---

## Objects & Type Aliases

- Type alias:
  ```typescript
  type User = { id: number; name: string; email?: string };
  ```
- Object:
  ```typescript
  const user: User = { id: 1, name: "Bob" };
  ```

---

## Union & Intersection Types

- Union:
  ```typescript
  let val: number | string;
  ```
- Intersection:
  ```typescript
  type Admin = { admin: true };
  type AdminUser = User & Admin;
  ```

---

## Literal Types

- Restrict to specific values:
  ```typescript
  type Status = "success" | "error";
  let s: Status = "success";
  ```

---

## Nullable Types

- Allow `null` or `undefined`:
  ```typescript
  let token: string | null = null;
  ```

---

## Optional Chaining

- Safe property access:
  ```typescript
  user.address?.street;
  config.logMessage?.("hi");
  ```

---

## Functions

- With types, optional/default params:
  ```typescript
  function pow(x: number, y: number = 2): number {
    return x ** y;
  }
  ```

---

## Interfaces

- Object/class contracts:
  ```typescript
  interface Vehicle {
    speed: number;
    start(): void;
  }
  class Car implements Vehicle {
    speed = 0;
    start() {
      this.speed = 1;
    }
  }
  ```

---

## Classes

- With types and access modifiers:
  ```typescript
  class Person {
    private name: string;
    constructor(name: string) {
      this.name = name;
    }
    greet(): string {
      return `Hi, ${this.name}`;
    }
  }
  ```

---

## Generics

- Reusable types:
  ```typescript
  function identity<T>(x: T): T {
    return x;
  }
  let num = identity<number>(5);
  ```

---

## Modules (Import/Export)

- Export:
  ```typescript
  export function foo() {}
  export default class Bar {}
  ```
- Import:
  ```typescript
  import { foo } from "./mod";
  import Bar from "./mod";
  ```

---

## Error Handling

- Try/catch:
  ```typescript
  try { ... } catch (e) { ... }
  ```

---

## Testing (Jest Example)

- Test:
  ```typescript
  test("adds", () => {
    expect(add(1, 2)).toBe(3);
  });
  ```
