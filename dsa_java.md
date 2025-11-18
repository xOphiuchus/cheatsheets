# Java Data Structures & Algorithms (DSA) Cheatsheet (Essential)

---

## Array & ArrayList

- Array: Fixed size.
- ArrayList: Dynamic size.

```java
int[] arr = {1,2,3};
ArrayList<Integer> list = new ArrayList<>();
list.add(4);
```

---

## Stack & Queue

- Stack: LIFO, use `Stack`.
- Queue: FIFO, use `Queue`/`LinkedList`.

```java
Stack<Integer> s = new Stack<>();
Queue<Integer> q = new LinkedList<>();
```

---

## LinkedList

- Node-based, dynamic size.

```java
LinkedList<Integer> ll = new LinkedList<>();
ll.add(1);
```

---

## HashMap

- Key-value lookup.

```java
HashMap<String, Integer> m = new HashMap<>();
m.put("a", 1);
```

---

## Tree

- Hierarchical, use class for nodes.

```java
class Node { int data; Node left, right; }
```

---

## Graph

- Nodes and edges, use adjacency list.

```java
ArrayList<Integer>[] adj = new ArrayList[10];
adj[0] = new ArrayList<>();
adj[0].add(1);
```

---

## Searching

- Linear: O(n), any list.
- Binary: O(log n), sorted array.

```java
int linear(int[] a, int x) { for(int i=0;i<a.length;i++) if(a[i]==x) return i; return -1; }
int binary(int[] a, int x) { int l=0,r=a.length-1; while(l<=r){int m=l+(r-l)/2;if(a[m]==x)return m;if(a[m]<x)l=m+1;else r=m-1;}return -1;}
```

---

## Sorting

- Use `Arrays.sort()` or `Collections.sort()`.

```java
Arrays.sort(arr);
Collections.sort(list);
```

---

## Recursion

- Function calls itself, base case required.

```java
int fact(int n) { return n==0 ? 1 : n*fact(n-1); }
```

---

## Dynamic Programming

- Store subproblem results.

```java
int[] dp = new int[n+1];
Arrays.fill(dp, -1);
int fib(int n) { if(n<=1) return n; if(dp[n]!=-1) return dp[n]; return dp[n]=fib(n-1)+fib(n-2);}
```

---
