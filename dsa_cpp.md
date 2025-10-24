# C++ Data Structures & Algorithms (DSA) Cheatsheet

---

## 1. What are Data Structures and Algorithms? 📈

**What it is:**  
Data structures are ways to organize and store data in a computer, enabling efficient access and modification. Algorithms are step-by-step procedures or sets of rules used to solve a specific problem. They work together: data structures hold the data, and algorithms process it.

**Why it's important:**  
They are the foundation of all software. Efficient data structures and algorithms lead to faster, more memory-friendly, and scalable programs.

**Basic usage:**

- Data structures: Choose based on the problem's needs (e.g., array, linked list).
- Algorithms: Design a set of instructions (e.g., search, sort) to manipulate the data.

**Key things to remember:**

- The choice of a data structure often dictates which algorithms are most efficient.
- There's no single "best" data structure or algorithm; the choice depends on the problem's requirements.

**Example use case:**  
A phonebook is a data structure (like a hash table) that stores names and numbers. A search algorithm is used to quickly find a number given a name.

---

## 2. Stacks 📚

**What it is:**  
A stack is a linear data structure that follows the LIFO (Last-In, First-Out) principle.

**Why it's important:**  
Used to manage function calls, handle backtracking, and evaluate expressions.

**Basic syntax and usage (C++ std::stack):**

```cpp
#include <stack>
#include <iostream>

std::stack<int> myStack;
myStack.push(10);
myStack.push(20);
myStack.push(30);

std::cout << myStack.top(); // 30
myStack.pop();

if (!myStack.empty()) {
  std::cout << myStack.top(); // 20
}
```

**Key things to remember:**

- Operations: push (add to top), pop (remove from top), top (view top element).
- Can't access elements in the middle directly.

**Example use case:**  
Web browser history: "Back" pops the current page and returns to the previous.

---

## 3. Queues 🎟️

**What it is:**  
A queue is a linear data structure that follows the FIFO (First-In, First-Out) principle.

**Why it's important:**  
Used for task scheduling, resource sharing, and managing I/O operations.

**Basic syntax and usage (C++ std::queue):**

```cpp
#include <queue>
#include <iostream>

std::queue<std::string> myQueue;
myQueue.push("Task 1");
myQueue.push("Task 2");
myQueue.push("Task 3");

std::cout << myQueue.front(); // Task 1
myQueue.pop();
std::cout << myQueue.front(); // Task 2
```

**Key things to remember:**

- Operations: push (add to back), pop (remove from front), front (view front element).
- Can't access elements in the middle directly.

**Example use case:**  
Print spooler: Documents are processed in the order submitted.

---

## 4. Priority Queues 🥇

**What it is:**  
A priority queue is a data structure where each element has a priority. Highest priority element is always at the front.

**Why it's important:**  
Used in algorithms like Dijkstra's shortest path, task scheduling.

**Basic syntax and usage (C++ std::priority_queue):**

```cpp
#include <queue>
#include <iostream>

std::priority_queue<int> pq;
pq.push(10);
pq.push(50);
pq.push(30);

std::cout << pq.top(); // 50
pq.pop();
std::cout << pq.top(); // 30
```

**Key things to remember:**

- Highest (or lowest) priority is always at the top.
- Default is max-heap (largest element has highest priority).

**Example use case:**  
OS task scheduling: High-priority processes run before low-priority ones.

---

## 5. Linked Lists 🔗

**What it is:**  
A linked list is a linear data structure where each node contains data and a pointer to the next node.

**Why it's important:**  
Great for frequent insertions and deletions.

**Basic syntax and usage:**

```cpp
#include <iostream>

struct Node {
    int data;
    Node* next;
};

Node* head = new Node();
head->data = 10;
head->next = nullptr;

Node* second = new Node();
second->data = 20;
second->next = nullptr;
head->next = second;

Node* current = head;
while (current != nullptr) {
    std::cout << current->data << " ";
    current = current->next;
}
```

**Key things to remember:**

- Nodes connected via pointers.
- Accessing by index is slow; insert/delete is fast with a pointer to the previous node.

**Example use case:**  
Music playlists: Easily add or remove songs.

---

## 6. Dynamic Arrays 🌱

**What it is:**  
A dynamic array can automatically resize itself (e.g., C++ std::vector).

**Why it's important:**  
Provides fast random access and flexible size.

**Basic syntax and usage (C++ std::vector):**

```cpp
#include <vector>
#include <iostream>

std::vector<int> myVector;
myVector.push_back(10);
myVector.push_back(20);
myVector.push_back(30);

std::cout << myVector[1]; // 20

for (int i : myVector) {
    std::cout << i << " ";
}
```

**Key things to remember:**

- Random access is fast ($O(1)$).
- Insertion/deletion at end is fast; in the middle is slow.

**Example use case:**  
Storing user-uploaded photos.

---

## 7. LinkedLists vs ArrayLists 🤼‍♂️

**What it is:**  
Comparison of linked list and dynamic array (ArrayList/vector).

**Key things to remember:**

| Feature         | Linked List               | Dynamic Array (Vector)    |
| --------------- | ------------------------- | ------------------------- |
| Memory          | Not contiguous            | Contiguous                |
| Access          | Slow ($O(n)$)             | Fast ($O(1)$)             |
| Insert/Delete   | Fast ($O(1)$ at position) | Slow ($O(n)$ in middle)   |
| Memory Overhead | Higher (pointer per node) | Lower                     |
| Use Case        | Frequent add/remove       | Frequent access/iteration |

**Example use case:**

- LinkedList: Undo history in a text editor.
- ArrayList: Displaying a list of students by index.

---

## 8. Big O Notation 📈

**What it is:**  
Describes the limiting behavior of an algorithm's running time or space as input size grows.

**Why it's important:**  
Allows comparison of algorithm efficiency.

**Basic usage:**

- $O(1)$: Constant time
- $O(n)$: Linear time
- $O(n^2)$: Quadratic time
- $O(\log n)$: Logarithmic time

**Key things to remember:**

- Describes worst-case performance.
- Focuses on dominant term.

**Example use case:**  
Comparing linear search ($O(n)$) vs binary search ($O(\log n)$).

---

## 9. Linear Search ⬇️

**What it is:**  
Checks each element until a match is found.

**Why it's important:**  
Works on any list, sorted or not.

**Basic syntax and usage:**

```cpp
int linearSearch(int arr[], int n, int target) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == target) return i;
    }
    return -1;
}
```

**Key things to remember:**

- Time complexity: $O(n)$.
- No need for sorted data.

**Example use case:**  
Finding a file in an unsorted list.

---

## 10. Binary Search 🪓

**What it is:**  
Efficient search for sorted lists by repeatedly dividing the interval in half.

**Why it's important:**  
Much faster than linear search for large, sorted datasets.

**Basic syntax and usage:**

```cpp
int binarySearch(int arr[], int left, int right, int target) {
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) return mid;
        if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
```

**Key things to remember:**

- List must be sorted.
- Time complexity: $O(\log n)$.

**Example use case:**  
Finding a word in a dictionary.

---

## 11. Interpolation Search ❓

**What it is:**  
Improvement over binary search for uniformly distributed data.

**Why it's important:**  
Can be faster than binary search for uniform data.

**Basic syntax and usage:**

```cpp
int interpolationSearch(int arr[], int n, int target) {
    int low = 0, high = n - 1;
    while (low <= high && target >= arr[low] && target <= arr[high]) {
        int pos = low + (((double)(high - low) / (arr[high] - arr[low])) * (target - arr[low]));
        if (arr[pos] == target) return pos;
        if (arr[pos] < target) low = pos + 1;
        else high = pos - 1;
    }
    return -1;
}
```

**Key things to remember:**

- List must be sorted and preferably uniform.
- Worst-case: $O(n)$, average: $O(\log\log n)$.

**Example use case:**  
Searching for a name in a phone book.

---

## 12. Bubble Sort 🤿

**What it is:**  
Simple sorting algorithm that repeatedly steps through the list, swapping adjacent elements if out of order.

**Why it's important:**  
Easy to understand, but inefficient.

**Basic syntax and usage:**

```cpp
void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) std::swap(arr[j], arr[j + 1]);
        }
    }
}
```

**Key things to remember:**

- Time complexity: $O(n^2)$.
- Stable sort.

**Example use case:**  
Teaching sorting basics.

---

## 13. Selection Sort 🔦

**What it is:**  
Finds the minimum element and moves it to the sorted part.

**Why it's important:**  
Simple, in-place, but inefficient for large lists.

**Basic syntax and usage:**

```cpp
void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int min_idx = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[min_idx]) min_idx = j;
        }
        std::swap(arr[i], arr[min_idx]);
    }
}
```

**Key things to remember:**

- Time complexity: $O(n^2)$.
- Fewest swaps among simple sorts.

**Example use case:**  
Educational purposes.

---

## 14. Insertion Sort 🧩

**What it is:**  
Builds the sorted array one item at a time.

**Why it's important:**  
Efficient for small or mostly sorted lists.

**Basic syntax and usage:**

```cpp
void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i], j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```

**Key things to remember:**

- Time complexity: $O(n^2)$ worst, $O(n)$ best.
- Stable and in-place.

**Example use case:**  
Sorting cards in your hand.

---

## 15. Recursion 😵

**What it is:**  
A function calls itself to solve a problem by breaking it into subproblems.

**Why it's important:**  
Elegant for problems with self-similar structure.

**Basic syntax and usage (factorial):**

```cpp
long long factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}
```

**Key things to remember:**

- Base case is essential.
- Can lead to stack overflow if too deep.

**Example use case:**  
Calculating factorial.

---

## 16. Merge Sort 🔪

**What it is:**  
Divide-and-conquer sorting algorithm: split, sort, and merge.

**Why it's important:**  
Efficient and stable, $O(n \log n)$ time.

**Basic usage:**

- Divide: Split array.
- Conquer: Recursively sort.
- Combine: Merge sorted halves.

**Key things to remember:**

- Time: $O(n \log n)$.
- Stable, but not in-place (needs extra memory).

**Example use case:**  
Sorting large datasets.

---

## 17. Quick Sort ⚡

**What it is:**  
Divide-and-conquer sorting: pick a pivot, partition, and recurse.

**Why it's important:**  
Very fast on average, often used in libraries.

**Basic usage:**

- Pivot: Choose element.
- Partition: Rearrange.
- Recurse: Sort subarrays.

**Key things to remember:**

- Average: $O(n \log n)$, worst: $O(n^2)$.
- In-place.

**Example use case:**  
In-memory array sorting.

---

## 18. Hash Tables #️⃣

**What it is:**  
Stores key-value pairs using a hash function (C++ `std::unordered_map`).

**Why it's important:**  
Fast $O(1)$ average-case for insert, delete, search.

**Basic syntax and usage:**

```cpp
#include <unordered_map>
#include <iostream>

std::unordered_map<std::string, int> scores;
scores["Alice"] = 95;
scores["Bob"] = 88;

std::cout << scores["Alice"]; // 95

if (scores.count("Charlie")) {
    std::cout << "Charlie found!";
} else {
    std::cout << "Charlie not found.";
}
```

**Key things to remember:**

- Collisions must be handled.
- Worst-case: $O(n)$, but rare.

**Example use case:**  
Dictionary or phonebook.

---

## 19. Graphs Intro 🌐

**What it is:**  
A graph is a set of vertices (nodes) and edges (connections).

**Why it's important:**  
Models relationships: social networks, maps, etc.

**Basic usage:**

- Vertices: nodes (e.g., cities)
- Edges: connections (e.g., roads)
- Directed/undirected

**Key things to remember:**

- Represented as adjacency matrix or list.

**Example use case:**  
Google Maps: cities and roads.

---

## 20. Adjacency Matrix ⬜

**What it is:**  
Graph representation using a 2D array.

**Why it's important:**  
Simple, fast edge checks.

**Basic usage:**

```cpp
#define V 4
int adjMatrix[V][V] = {
    {0, 1, 1, 0},
    {1, 0, 0, 1},
    {1, 0, 0, 1},
    {0, 1, 1, 0}
};

if (adjMatrix[0][2] == 1) {
    // Edge exists
}
```

**Key things to remember:**

- Edge check: $O(1)$.
- Space: $O(V^2)$ (bad for sparse graphs).

**Example use case:**  
Dense social network.

---

## 21. Adjacency List 📑

**What it is:**  
Graph representation using an array of lists/vectors.

**Why it's important:**  
Space-efficient for sparse graphs.

**Basic usage:**

```cpp
#define V 4
std::vector<int> adjList[V];

void addEdge(int u, int v) {
    adjList[u].push_back(v);
    adjList[v].push_back(u); // Undirected
}

addEdge(0, 1);
addEdge(0, 2);
addEdge(1, 3);
addEdge(2, 3);

for (int neighbor : adjList[0]) {
    // ...
}
```

**Key things to remember:**

- Space: $O(V + E)$.
- Edge check: $O(k)$ (k = neighbors).

**Example use case:**  
Web links (sparse graph).

---

## 22. Depth First Search (DFS) ⬇️

**What it is:**  
Graph traversal: explores as far as possible along each branch before backtracking.

**Why it's important:**  
Used for paths, cycles, topological sort.

**Basic syntax and usage:**

```cpp
void dfs(int startNode, std::vector<int> adjList[], bool visited[]) {
    visited[startNode] = true;
    for (int neighbor : adjList[startNode]) {
        if (!visited[neighbor]) dfs(neighbor, adjList, visited);
    }
}
```

**Key things to remember:**

- Time: $O(V + E)$.

**Example use case:**  
Maze solving.

---

## 23. Breadth First Search (BFS) ↔️

**What it is:**  
Graph traversal: explores all neighbors at current depth before going deeper.

**Why it's important:**  
Finds shortest path in unweighted graphs.

**Basic syntax and usage:**

```cpp
void bfs(int startNode, std::vector<int> adjList[]) {
    // ... setup queue and visited array
    q.push(startNode);
    visited[startNode] = true;
    while (!q.empty()) {
        int currentNode = q.front();
        q.pop();
        for (int neighbor : adjList[currentNode]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}
```

**Key things to remember:**

- Time: $O(V + E)$.
- Guarantees shortest path in unweighted graphs.

**Example use case:**  
Social network connections.

---

## 24. Tree Data Structure Intro 🌳

**What it is:**  
A hierarchical, non-linear data structure with nodes and edges.

**Why it's important:**  
Represents hierarchies (file systems, org charts).

**Key things to remember:**

- Root, child, parent, leaf.
- No cycles.

**Example use case:**  
File system directory tree.

---

## 25. Binary Search Tree (BST) 🔍

**What it is:**  
A binary tree where left < root < right.

**Why it's important:**  
Efficient search, insert, delete ($O(\log n)$ average).

**Basic usage:**

```cpp
struct Node {
    int data;
    Node* left;
    Node* right;
};
// Insert/search: go left if less, right if more.
```

**Key things to remember:**

- Can become skewed ($O(n)$ worst).

**Example use case:**  
Sorted key-value map.

---

## 26. Tree Traversal 🧗

**What it is:**  
Visiting each node in a tree (inorder, preorder, postorder).

**Why it's important:**  
Different traversals for different applications.

**Basic usage:**

```cpp
// Inorder: Left -> Root -> Right
void inorder(Node* node) {
    if (!node) return;
    inorder(node->left);
    std::cout << node->data << " ";
    inorder(node->right);
}
// Preorder: Root -> Left -> Right
void preorder(Node* node) { /* ... */ }
// Postorder: Left -> Right -> Root
void postorder(Node* node) { /* ... */ }
```

**Key things to remember:**

- Inorder on BST gives sorted order.

**Example use case:**  
Printing BST in order.

---

## 27. Calculate Execution Time ⏱️

**What it is:**  
Measuring how long code takes to run (C++ chrono).

**Why it's important:**  
Compare real-world efficiency.

**Basic syntax and usage:**

```cpp
#include <iostream>
#include <chrono>

int main() {
    auto start = std::chrono::high_resolution_clock::now();
    // ... code ...
    auto end = std::chrono::high_resolution_clock::now();
    std::chrono::duration<double> duration = end - start;
    std::cout << "Execution time: " << duration.count() << " seconds";
    return 0;
}
```

**Key things to remember:**

- Real time depends on machine, compiler, etc.
- Big O is theoretical; timing is practical.

**Example use case:**  
Comparing custom sort vs std::sort.

---
