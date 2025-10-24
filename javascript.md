# JavaScript Cheatsheet

---

## Variables (var, let, const)

- **Declare:**
  ```js
  let x = 10;
  const y = "hi";
  var z = true;
  ```
- **Key:** Prefer `const` for constants, `let` for block scope.

---

## Data Types

- **Types:** Number, String, Boolean, Array, Object, Null, Undefined, BigInt, Symbol.
- **Check:**
  ```js
  typeof x;
  ```
- **Key:** JS is dynamically typed.

---

## Operators

- **Arithmetic:** `+ - * / %`
- **Comparison:** `== === != !== < > <= >=`
- **Logical:** `&& || !`
- **Assignment:** `= += -= *= /=`
- **Key:** Use `===` for strict equality.

---

## Type Conversion

- **Convert:**
  ```js
  Number("123");
  String(456);
  parseInt("100px");
  parseFloat("3.14");
  ```
- **Key:** `Number("abc")` is `NaN`.

---

## Control Flow (If/Else, Switch)

- **If/Else:**
  ```js
  if (x > 0) { ... } else { ... }
  ```
- **Switch:**
  ```js
  switch (val) {
    case 1: ...; break;
    default: ...;
  }
  ```
- **Key:** Use `break` in switch.

---

## Loops (While, For, For...of)

- **For:**
  ```js
  for (let i = 0; i < 5; i++) { ... }
  ```
- **While:**
  ```js
  while (cond) { ... }
  ```
- **For...of:**
  ```js
  for (const item of arr) { ... }
  ```
- **Key:** Use for arrays/iterables.

---

## Functions

- **Declaration:**
  ```js
  function foo(x) {
    return x + 1;
  }
  ```
- **Expression:**
  ```js
  const add = function (a, b) {
    return a + b;
  };
  ```
- **Arrow:**
  ```js
  const mul = (x, y) => x * y;
  ```
- **Key:** Arrow functions inherit `this` from parent.

---

## Arrays

- **Create:**
  ```js
  let arr = [1, 2, 3];
  arr.push(4);
  arr.pop();
  arr.slice(1, 3);
  arr.map((x) => x * 2);
  ```
- **Key:** Zero-indexed, dynamic size.

---

## Objects & this

- **Create:**
  ```js
  let obj = { a: 1, b: 2 };
  obj.c = 3;
  ```
- **Method:**
  ```js
  obj.say = function () {
    return this.a;
  };
  ```
- **Key:** `this` refers to the object in regular functions.

---

## Classes (ES6+)

- **Syntax:**
  ```js
  class Animal {
    constructor(name) {
      this.name = name;
    }
    speak() {
      return `${this.name} speaks`;
    }
  }
  class Dog extends Animal {
    speak() {
      return `${this.name} barks`;
    }
  }
  ```
- **Key:** Use `extends` for inheritance, `super()` for parent constructor.

---

## Asynchronous Code (Callbacks, Promises, Async/Await)

- **Promise:**
  ```js
  function fetchData() {
    return new Promise((resolve, reject) => { ... });
  }
  fetchData().then(data => ...).catch(err => ...);
  ```
- **Async/Await:**
  ```js
  async function getData() {
    try {
      let data = await fetchData();
    } catch (e) { ... }
  }
  ```
- **Key:** Use `await` inside `async` functions.

---

## Error Handling

- **Try/Catch:**
  ```js
  try { ... } catch (e) { ... } finally { ... }
  ```
- **Throw:**
  ```js
  throw new Error("msg");
  ```
- **Key:** Use `.catch()` for Promise errors.

---

## ES6 Modules (Import/Export)

- **Export:**
  ```js
  export const PI = 3.14;
  export default function () {}
  ```
- **Import:**
  ```js
  import { PI } from "./mod.js";
  import fn from "./mod.js";
  ```
- **Key:** Named exports use `{}`, default exports no braces.

---

## Testing (Jest Example)

- **Test:**
  ```js
  test("adds", () => {
    expect(add(1, 2)).toBe(3);
  });
  ```
- **Key:** Use `describe` for grouping, `expect` for assertions.

---

## Key JS Methods

- **Array:**  
  `.map()`, `.filter()`, `.reduce()`, `.forEach()`
- **String:**  
  `.length`, `.trim()`, `.toUpperCase()`, `.slice()`
- **Key:** Non-mutating methods return new values.
