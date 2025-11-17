# Rust Data Structures & Algorithms (DSA) Cheatsheet
Last Updated : 10 Oct, 2025

1. Array & Vec
Vec is the dynamic array type in Rust.

```rust
let arr = [10,20,30];
let mut v = vec![10,20,30];
v.push(40);
println!("{:?} {:?}", arr, v);
```

2. Searching & Sorting
Binary search on sorted slices with binary_search, sort via sort().

```rust
let mut v = vec![5,3,8,1];
v.sort();
let pos = v.binary_search(&3);
```

3. Strings
String and &str; use String::from and push_str.

4. HashSet & HashMap
Use std::collections::{HashSet, HashMap}.

5. Stack & Queue
Vec as stack; VecDeque as queue.

6. Linked List, Tree, Graph
Linked list (Vec or Box based), graphs with adjacency Vec<Vec<usize>>.

7. Heap
BinaryHeap for max heap; use Reverse for min-heap.

8. DP
Use Vec<Option<T>> for memoization.

