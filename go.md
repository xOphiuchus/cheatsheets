# Go Cheatsheet

---

## Package

Defines code scope and visibility.

```go
package main // or utils
```

- `main` for executables.
- Only capitalized names exported.

---

## Import & Alias

Bring in other packages.

```go
import "fmt"
import myio "fmt"
```

- Unused imports = error.
- Alias for brevity or conflicts.

---

## Comments

Explain code.

```go
// Single line
/* Multi-line */
```

- Comments before declarations generate docs.

---

## Main

Program entry point.

```go
func main() { fmt.Println("Hi") }
```

- Must be in `main` package.

---

## User Input

Read from stdin.

```go
var name string
fmt.Scanln(&name)
```

- Use `&` for Scanln.

---

## Error Handling

Go uses explicit errors.

```go
val, err := f()
if err != nil { return }
```

- Always check errors.

---

## Variables & Types

Declare and assign.

```go
var n int = 1
s := "hi"
const PI = 3.14
```

- Statically typed, zero values.

---

## Casting

Convert types.

```go
f := float64(10)
```

- No implicit conversion.

---

## If / For / Range

Control flow.

```go
if x > 0 { ... }
for i := 0; i < 3; i++ { ... }
for i, v := range arr { ... }
```

- No parentheses.

---

## Arrays & Slices

Collections.

```go
a := [3]int{1,2,3}
s := []int{1,2,3}
s = append(s, 4)
```

- Slices are dynamic.

---

## Functions

Reusable code.

```go
func add(a, b int) int { return a + b }
```

- Multiple returns: `func f() (int, error)`

---

## Pointers

Reference values.

```go
p := &x
*p = 2
```

- Use for modifying caller's data.

---

## Maps

Key-value store.

```go
m := map[string]int{"a": 1}
v, ok := m["a"]
```

- Use `ok` to check existence.

---

## Structs & Methods

Custom types.

```go
type T struct { X int }
func (t T) Foo() {}
```

- Capitalized fields/methods are exported.

---

## Interfaces

Behavior contracts.

```go
type Sayer interface { Say() string }
```

- Satisfied implicitly.

---

## Goroutines & Channels

Concurrency.

```go
go f()
ch := make(chan int)
ch <- 1; x := <-ch
```

- Use channels to sync goroutines.

---

## Mutex

Lock for shared data.

```go
var mu sync.Mutex
mu.Lock(); x++; mu.Unlock()
```

- Use `defer mu.Unlock()`.

---

## File IO

Read/write files.

```go
data, _ := ioutil.ReadFile("f.txt")
ioutil.WriteFile("f.txt", data, 0644)
```

- Always check errors in real code.

---

## Testing

Automated tests.

```go
func TestX(t *testing.T) { ... }
```

- Files end with `_test.go`.

---

## Web Server

Minimal HTTP server.

```go
http.HandleFunc("/", func(w, r) { fmt.Fprint(w, "Hi") })
http.ListenAndServe(":8080", nil)
```

---

## Install

- Download: [golang.org/dl](https://golang.org/dl)
- Run: `go run main.go`
- Build: `go build main.go`

---
