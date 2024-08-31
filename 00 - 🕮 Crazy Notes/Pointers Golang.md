2024/06/24 10:21
Status: #idea
Tags: [[01 - Classes/CSE 4600 - Operating Systems/Memory Management|Memory Management]]


## Pointer Syntax in Go (Golang)

### Introduction
- In Go, pointers hold the memory address of a variable. Unlike C++, Go does not support pointer arithmetic, which can lead to safer and more secure code.

### Creating Pointers
- A pointer is created by using the `&` operator to find the address of a variable.

#### Example: Creating a Pointer

```go
var a int = 58
var p *int = &a  // p holds the address of a
```

### Dereferencing Pointers

- Dereferencing a pointer means accessing the value at the memory address held by the pointer. This is done using the `*` operator.

#### Example: Dereferencing a Pointer

```go
var value int = *p  // value now holds the value of a, which is 58
```

### Changing Value via Pointer

- You can change the value at the address the pointer is pointing to by dereferencing the pointer and assigning a new value.

#### Example: Changing Value

```go
*p = 100  // changes the value of a to 100
```

### Nil Pointers

- A pointer that is nil holds no memory address. Dereferencing a nil pointer will cause a runtime panic, which is a common source of bugs.

#### Example: Nil Pointer

```go
var ptr *int  // ptr is nil by default
// *ptr = 100  // uncommenting this line will cause a runtime panic
```

### Use of `new` Function

- The `new` function allocates space for a variable of a given type, initializes it to zero, and returns a pointer to it.

#### Example: Using `new`

```go
ptr := new(int)  // allocates memory for an integer, initializes it to 0
*ptr = 90        // sets the value of the allocated integer to 90
```

### Pointers to Structs

- Pointers can also point to structs, allowing you to modify struct fields.

#### Example: Pointers to Structs

```go
type Person struct {
    Name string
    Age  int
}

bob := &Person{"Bob", 30}  // bob is a pointer to a Person struct
bob.Age = 31               // modifies the Age field of the struct
```

### Conclusion

Pointers in Go provide powerful functionality for manipulating data and controlling memory usage, crucial for tasks that require low-level system interaction. Understanding pointers and their correct usage is essential for effective programming in Go.


---
# References
