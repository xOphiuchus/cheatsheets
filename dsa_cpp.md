# C++ Data Structures & Algorithms (DSA) Cheatsheet (Essential)

---

## Array & Vector

- Array: Fixed size, fast access.
- Vector: Dynamic size, STL container.

```cpp
int arr[5] = {1,2,3,4,5};
std::vector<int> v = {1,2,3};
v.push_back(4);
```

---

## Stack & Queue

- Stack: LIFO, use `std::stack`.
- Queue: FIFO, use `std::queue`.

```cpp
std::stack<int> s; s.push(1); s.pop();
std::queue<int> q; q.push(1); q.pop();
```

---

## Linked List

- Node-based, dynamic size, fast insert/delete.

```cpp
struct Node { int data; Node* next; };
Node* head = new Node{1, nullptr};
```

---

## Hash Table

- Fast key-value lookup, use `std::unordered_map`.

```cpp
std::unordered_map<std::string, int> m;
m["a"] = 1;
```

---

## Tree

- Hierarchical, use struct/class for nodes.

```cpp
struct Node { int data; Node* left; Node* right; };
```

---

## Graph

- Nodes and edges, use adjacency list.

```cpp
std::vector<int> adj[10];
adj[0].push_back(1);
```

---

## Searching

- Linear: O(n), any list.
- Binary: O(log n), sorted list.

```cpp
int linear(int a[], int n, int x) { for(int i=0;i<n;i++) if(a[i]==x) return i; return -1; }
int binary(int a[], int l, int r, int x) { while(l<=r){int m=l+(r-l)/2;if(a[m]==x)return m;if(a[m]<x)l=m+1;else r=m-1;}return -1;}
```

---

## Sorting

- Bubble, Selection, Insertion, Quick, Merge.

```cpp
std::sort(v.begin(), v.end());
```

---

## Recursion

- Function calls itself, base case required.

```cpp
int fact(int n) { return n==0 ? 1 : n*fact(n-1); }
```

---

## Dynamic Programming

- Store subproblem results, avoid recomputation.

```cpp
std::vector<int> dp(n+1, -1);
int fib(int n) { if(n<=1) return n; if(dp[n]!=-1) return dp[n]; return dp[n]=fib(n-1)+fib(n-2);}
```

---
