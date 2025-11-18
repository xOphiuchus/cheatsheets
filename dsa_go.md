# Go Data Structures & Algorithms (DSA) Cheatsheet (Essential)

---

## Array & Slice

- Array: Fixed size.
- Slice: Dynamic size.

```go
arr := [3]int{1,2,3}
slice := []int{1,2,3}
slice = append(slice, 4)
```

---

## Stack & Queue

- Stack: Use slice, push/pop.
- Queue: Use slice or channel.

```go
stack := []int{}
stack = append(stack, 1)
stack = stack[:len(stack)-1]

queue := []int{}
queue = append(queue, 1)
queue = queue[1:]
```

---

## Map

- Key-value lookup.

```go
m := map[string]int{"a":1}
```

---

## Linked List

- Use container/list.

```go
import "container/list"
l := list.New()
l.PushBack(1)
```

---

## Tree

- Use struct for nodes.

```go
type Node struct { Data int; Left, Right *Node }
```

---

## Graph

- Adjacency list.

```go
adj := make([][]int, 10)
adj[0] = append(adj[0], 1)
```

---

## Searching

- Linear: O(n).
- Binary: O(log n), sorted slice.

```go
func linear(a []int, x int) int { for i,v := range a { if v==x { return i } } ; return -1 }
func binary(a []int, x int) int { l,r := 0,len(a)-1; for l<=r { m := l+(r-l)/2; if a[m]==x { return m } ; if a[m]<x { l=m+1 } else { r=m-1 } } ; return -1 }
```

---

## Sorting

- Use sort package.

```go
import "sort"
sort.Ints(slice)
```

---

## Recursion

- Function calls itself, base case required.

```go
func fact(n int) int { if n==0 { return 1 } ; return n*fact(n-1) }
```

---

## Dynamic Programming

- Store subproblem results.

```go
dp := make([]int, n+1)
for i := range dp { dp[i] = -1 }
func fib(n int) int { if n<=1 { return n } ; if dp[n]!=-1 { return dp[n] } ; dp[n]=fib(n-1)+fib(n-2); return dp[n] }
```

---
