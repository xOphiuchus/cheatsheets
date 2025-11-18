# Rust Data Structures & Algorithms (DSA) Cheatsheet (Essential)

Last Updated : 10 Oct, 2025

---

## Array & Vec

- Array: Fixed size.
- Vec: Dynamic size.

```rust
let arr = [1,2,3];
let mut v = vec![1,2,3];
v.push(4);
```

---

## Stack & Queue

- Stack: Use Vec, push/pop.
- Queue: Use VecDeque.

```rust
let mut stack = Vec::new();
stack.push(1); stack.pop();

use std::collections::VecDeque;
let mut queue = VecDeque::new();
queue.push_back(1); queue.pop_front();
```

---

## HashMap

- Key-value lookup.

```rust
use std::collections::HashMap;
let mut m = HashMap::new();
m.insert("a", 1);
```

---

## Linked List

- Use Vec or Box for nodes.

```rust
struct Node { data: i32, next: Option<Box<Node>> }
```

---

## Tree

- Use struct for nodes.

```rust
struct Node { data: i32, left: Option<Box<Node>>, right: Option<Box<Node>> }
```

---

## Graph

- Adjacency list.

```rust
let mut adj = vec![vec![]; 10];
adj[0].push(1);
```

---

## Searching

- Linear: O(n).
- Binary: O(log n), sorted slice.

```rust
fn linear(a: &[i32], x: i32) -> Option<usize> { a.iter().position(|&v| v==x) }
fn binary(a: &[i32], x: i32) -> Option<usize> { a.binary_search(&x).ok() }
```

---

## Sorting

- Use sort().

```rust
let mut v = vec![5,3,8,1];
v.sort();
```

---

## Recursion

- Function calls itself, base case required.

```rust
fn fact(n: u32) -> u32 { if n==0 { 1 } else { n*fact(n-1) } }
```

---

## Dynamic Programming

- Store subproblem results.

```rust
fn fib(n: usize, dp: &mut [i32]) -> i32 {
    if n<=1 { return n as i32; }
    if dp[n]!=-1 { return dp[n]; }
    dp[n]=fib(n-1,dp)+fib(n-2,dp); dp[n]
}
let mut dp = vec![-1; 11];
fib(10, &mut dp);
```

---
