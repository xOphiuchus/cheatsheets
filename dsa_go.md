# Go Data Structures & Algorithms (DSA) Cheatsheet
Last Updated : 10 Oct, 2025

1. Array & Slice
Go arrays (fixed) and slices (dynamic).

```go
package main
import "fmt"
func main() {
    arr := [5]int{10,20,30,40,50}
    slice := []int{10,20,30}
    slice = append(slice, 40)
    fmt.Println("Array:", arr)
    fmt.Println("Slice:", slice)
}
```

2. Searching & Sorting
sort package and manual loops.

```go
import "sort"
sort.Ints(slice)
```

3. String
string and strings.Builder.

4. Set & Map
Use map[T]struct{} as set; map[T]U for maps.

```go
m := map[string]int{"a":1}
set := map[int]struct{}{3:{}}
```

5. Queue, Stack & Linked List
Use slices or container/list for linked lists, use channels or slices for queues.

6. Tree & Graph
Use struct nodes and slices for adjacency lists.

7. Heap
container/heap for custom heaps.

8. Dynamic Programming
Use slices for memoization.

