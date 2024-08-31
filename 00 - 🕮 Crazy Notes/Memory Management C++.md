2024/06/24 10:04
Status: #idea
Tags: [[01 - Classes/CSE 4600 - Operating Systems/Memory Management|Memory Management]]

## Memory Management in C++

### Introduction
- C++ provides extensive support for memory management at the programmer's discretion, allowing for detailed control over system resources. This flexibility can lead to powerful, efficient code but requires careful management to avoid memory leaks and other issues.

### Core Concepts

1. **Dynamic Memory Allocation**
   - C++ uses the `new` and `delete` operators for dynamic memory allocation and deallocation. This allows for the creation of variables and arrays whose sizes need not be known until runtime.

2. **Smart Pointers**
   - Introduced in C++11, smart pointers automatically manage memory, helping to ensure that memory is properly cleaned up when it is no longer needed, thus preventing memory leaks. Examples include `std::unique_ptr`, `std::shared_ptr`, and `std::weak_ptr`.

### Syntax for Dynamic Memory Management

#### Using `new` and `delete`

- **Single Variable Allocation**
 
```cpp
  int* ptr = new int;  // dynamically allocates an integer
  *ptr = 5;            // assigns 5 to the allocated integer
  delete ptr;          // frees the allocated memory
  ptr = nullptr;       // sets ptr to point to nowhere
```

- **Array Allocation**

```cpp
int* array = new int[10];  // dynamically allocates an array of 10 integers
for(int i = 0; i < 10; i++) {
    array[i] = i * 2;      // initialize array elements
}
delete[] array;            // frees the allocated array
array = nullptr;           // helps prevent dangling pointers
```

#### Using Smart Pointers

- **Unique Pointers**

```cpp
#include <memory>
std::unique_ptr<int> ptr(new int);
*ptr = 7;  // use the pointer as a normal pointer
```

- **Shared Pointer**

```cpp
std::shared_ptr<int> sharedOne = std::make_shared<int>(10);
std::shared_ptr<int> sharedTwo = sharedOne;  // Both point to the same integer
// The integer will be deleted only when both sharedOne and sharedTwo are out of scope or reassigned.
```

### Memory Management Best Practices

- **Avoid Raw Pointers for Ownership**: Use smart pointers instead of raw pointers when the pointer needs to own the resource.
- **Resource Acquisition Is Initialization (RAII)**: Utilize constructor/destructor pairs to manage resources, ensuring that resources are properly released when an object is destroyed.
- **Check for Null before Deleting**: Always ensure that a pointer is not null before calling `delete` to avoid undefined behavior.
- **Avoid Memory Leaks**: Regularly check for memory leaks using tools like Valgrind or static analysis tools.

### Conclusion

Proper memory management in C++ is crucial for building efficient, reliable, and safe applications. By understanding and utilizing the tools and practices available in C++, developers can significantly enhance the robustness of their software.


---
# References

- [[Memory Management General|Memory Management General]]
- [[Memory Management GoLang]]