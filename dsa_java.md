# Java Data Structures & Algorithms (DSA) Cheatsheet

---

## 1. What are Data Structures and Algorithms? 📈

**What it is:**  
Ways to organize data (structures) and steps to process it (algorithms).

**Why it's important:**  
Foundation for efficient, scalable software.

**Key things to remember:**

- Choose the right structure for the problem.
- No universal "best" structure/algorithm.

**Example:**  
A `HashMap` stores names and numbers; a search algorithm finds a number by name.

---

## 2. Stacks 📚

**What it is:**  
LIFO (Last-In, First-Out) structure.

**Why it's important:**  
Used for function calls, undo, parsing.

**Usage:**

```java
Stack<Integer> stack = new Stack<>();
stack.push(10);
stack.push(20);
int top = stack.peek(); // 20
stack.pop();
```

**Key:**  
Only access top; no middle access.

**Example:**  
Browser back button.

---

## 3. Queues 🎟️

**What it is:**  
FIFO (First-In, First-Out) structure.

**Why it's important:**  
Task scheduling, resource sharing.

**Usage:**

```java
Queue<String> queue = new LinkedList<>();
queue.add("A");
queue.add("B");
String front = queue.peek(); // "A"
queue.remove();
```

**Key:**  
Add at end, remove from front.

**Example:**  
Print jobs.

---

## 4. Priority Queues 🥇

**What it is:**  
Elements served by priority.

**Why it's important:**  
Scheduling, algorithms like Dijkstra.

**Usage:**

```java
PriorityQueue<Integer> pq = new PriorityQueue<>();
pq.add(10);
pq.add(50);
pq.add(30);
int top = pq.peek(); // 10 (min-heap by default)
pq.remove();
```

**Key:**  
Java's `PriorityQueue` is min-heap by default.

**Example:**  
OS process scheduling.

---

## 5. Linked Lists 🔗

**What it is:**  
Nodes linked by references.

**Why it's important:**  
Efficient insert/delete.

**Usage:**

```java
LinkedList<Integer> list = new LinkedList<>();
list.add(10);
list.add(20);
for (int n : list) { System.out.println(n); }
```

**Key:**  
No random access; fast insert/remove.

**Example:**  
Music playlist.

---

## 6. Dynamic Arrays 🌱

**What it is:**  
Resizable arrays (`ArrayList`).

**Why it's important:**  
Random access, flexible size.

**Usage:**

```java
ArrayList<Integer> arr = new ArrayList<>();
arr.add(10);
arr.add(20);
int x = arr.get(1); // 20
```

**Key:**  
Fast access, slow insert/delete in middle.

**Example:**  
User-uploaded photos.

---

## 7. LinkedList vs ArrayList 🤼‍♂️

| Feature       | LinkedList          | ArrayList       |
| ------------- | ------------------- | --------------- |
| Memory        | Not contiguous      | Contiguous      |
| Access        | Slow O(n)           | Fast O(1)       |
| Insert/Delete | Fast at ends        | Slow in middle  |
| Use Case      | Frequent add/remove | Frequent access |

---

## 8. Big O Notation 📈

- $O(1)$: Constant
- $O(n)$: Linear
- $O(n^2)$: Quadratic
- $O(\log n)$: Logarithmic

**Key:**  
Describes worst-case, dominant term.

---

## 9. Linear Search ⬇️

**Usage:**

```java
for (int i = 0; i < arr.length; i++)
    if (arr[i] == target) return i;
```

**Key:**  
O(n), works on any list.

---

## 10. Binary Search 🪓

**Usage:**

```java
int l = 0, r = arr.length-1;
while (l <= r) {
    int m = l + (r-l)/2;
    if (arr[m] == target) return m;
    if (arr[m] < target) l = m+1; else r = m-1;
}
```

**Key:**  
O(log n), needs sorted array.

---

## 11. Interpolation Search ❓

**Usage:** (for uniform data)

```java
int low = 0, high = arr.length-1;
while (low <= high && target >= arr[low] && target <= arr[high]) {
    int pos = low + (high-low) * (target-arr[low]) / (arr[high]-arr[low]);
    if (arr[pos] == target) return pos;
    if (arr[pos] < target) low = pos+1; else high = pos-1;
}
```

**Key:**  
Best for uniform data.

---

## 12. Bubble Sort 🤿

**Usage:**

```java
for (int i = 0; i < n-1; i++)
    for (int j = 0; j < n-i-1; j++)
        if (arr[j] > arr[j+1]) swap(arr, j, j+1);
```

**Key:**  
O(n^2), stable, educational.

---

## 13. Selection Sort 🔦

**Usage:**

```java
for (int i = 0; i < n-1; i++) {
    int min = i;
    for (int j = i+1; j < n; j++)
        if (arr[j] < arr[min]) min = j;
    swap(arr, i, min);
}
```

**Key:**  
O(n^2), fewest swaps.

---

## 14. Insertion Sort 🧩

**Usage:**

```java
for (int i = 1; i < n; i++) {
    int key = arr[i], j = i-1;
    while (j >= 0 && arr[j] > key) arr[j+1] = arr[j--];
    arr[j+1] = key;
}
```

**Key:**  
O(n^2), good for small/mostly sorted.

---

## 15. Recursion 😵

**Usage:**

```java
int fact(int n) { return n == 0 ? 1 : n * fact(n-1); }
```

**Key:**  
Base case required.

---

## 16. Merge Sort 🔪

- Divide, sort, merge.
- O(n log n), stable.

---

## 17. Quick Sort ⚡

- Pick pivot, partition, recurse.
- O(n log n) avg, O(n^2) worst, in-place.

---

## 18. Hash Tables #️⃣

**Usage:**

```java
HashMap<String, Integer> map = new HashMap<>();
map.put("Alice", 95);
int score = map.get("Alice");
```

**Key:**  
O(1) average, handles collisions.

---

## 19. Graphs Intro 🌐

- Vertices (nodes), edges (connections).
- Represented as adjacency matrix/list.

---

## 20. Adjacency Matrix ⬜

**Usage:**

```java
int[][] matrix = new int[V][V];
if (matrix[0][2] == 1) { /* edge exists */ }
```

**Key:**  
O(1) edge check, O(V^2) space.

---

## 21. Adjacency List 📑

**Usage:**

```java
List<List<Integer>> adj = new ArrayList<>();
for (int i = 0; i < V; i++) adj.add(new ArrayList<>());
adj.get(0).add(1); // edge 0-1
```

**Key:**  
O(V+E) space, good for sparse graphs.

---

## 22. DFS ⬇️

**Usage:**

```java
void dfs(int v, boolean[] vis, List<List<Integer>> adj) {
    vis[v] = true;
    for (int u : adj.get(v)) if (!vis[u]) dfs(u, vis, adj);
}
```

**Key:**  
O(V+E), explores deep first.

---

## 23. BFS ↔️

**Usage:**

```java
Queue<Integer> q = new LinkedList<>();
boolean[] vis = new boolean[V];
q.add(start); vis[start] = true;
while (!q.isEmpty()) {
    int v = q.poll();
    for (int u : adj.get(v)) if (!vis[u]) { vis[u]=true; q.add(u); }
}
```

**Key:**  
O(V+E), finds shortest path in unweighted graphs.

---

## 24. Trees 🌳

- Hierarchical, no cycles.
- Root, parent, child, leaf.

---

## 25. Binary Search Tree (BST) 🔍

- Left < root < right.
- O(log n) avg, O(n) worst.

---

## 26. Tree Traversal 🧗

**Inorder:** left, root, right  
**Preorder:** root, left, right  
**Postorder:** left, right, root

---

## 27. Execution Time ⏱️

**Usage:**

```java
long start = System.nanoTime();
// ... code ...
long end = System.nanoTime();
System.out.println((end-start)/1e6 + " ms");
```

**Key:**  
Use for benchmarking.

---
