`std::stack` is a container adaptor that provides a LIFO (Last-In, First-Out) data structure. It acts as a wrapper around an underlying container, offering only a limited set of functions to maintain the stack structure. By default, `std::deque` is used as the underlying container, but `std::vector` or `std::list` can also be used. Elements are pushed and popped from the back (top) of the stack.

<br>

---

<br>

## Header File

To use `std::stack`, include the following header:

```cpp
#include <stack>
```

<br>

---

<br>

## Time/Space Complexities Summary

| Operation                | Time Complexity  | Space Complexity |
|--------------------------|------------------|------------------|
| Constructor (default)     | O(1)             | O(1)             |
| Constructor (range)       | O(n)             | O(n)             |
| push()                   | O(1) amortized   | O(1)             |
| pop()                    | O(1)             | O(1)             |
| top()                    | O(1)             | O(1)             |
| size()                   | O(1)             | O(1)             |
| empty()                  | O(1)             | O(1)             |
| swap()                   | O(1)             | O(1)             |

<br>

---

<br>

## Constructor

<br>

### std::stack()

**Description:** Constructs an empty stack.

**Template Syntax:**

```cpp
std::stack<data_type> stack_name;
```

- `data_type`: The type of the elements stored in the stack.
- `stack_name`: The name of the stack.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::stack<int> stk;
```

<br>

### std::stack(InputIt first, InputIt last)

**Description:** Constructs a stack from a range defined by iterators `[first, last)`.

**Template Syntax:**

```cpp
std::stack<data_type> stack_name(iterator_first, iterator_last);
```

- `data_type`: The type of the elements stored in the stack.
- `stack_name`: The name of the stack.
- `iterator_first`, `iterator_last`: Iterators defining the range of elements to insert.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::vector<int> vec = {1, 2, 3};
std::stack<int> stk(std::deque<int>(vec.begin(), vec.end()));
```

<br>

---

<br>

## Capacity Functions

<br>

### size()

**Description:** Returns the number of elements in the stack.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::stack<int> stk = {{1, 2, 3}};
size_t sz = stk.size(); // sz = 3
```

<br>

### empty()

**Description:** Checks if the stack is empty.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::stack<int> stk;
bool is_empty = stk.empty(); // true
```

<br>

---

<br>

## Element Access

<br>

### top()

**Description:** Accesses the top element of the stack.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::stack<int> stk = {1, 2, 3};
int top_element = stk.top(); // top_element = 3
```

<br>

---

<br>

## Modifiers

<br>

### push(const T& value)

**Description:** Pushes an element onto the stack.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) amortized | O(1) |

```cpp
std::stack<int> stk;
stk.push(4);  // Pushes 4 onto the stack
```

<br>

### emplace(Args&&... args)

**Description:** Constructs and inserts an element at the top of the stack.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::stack<int> stk;
stk.emplace(5);  // Constructs and pushes 5 onto the stack
```

<br>

### pop()

**Description:** Removes the top element from the stack.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::stack<int> stk = {1, 2, 3};
stk.pop();  // Removes the top element (3)
```

<br>

### swap(std::stack& other)

**Description:** Swaps the contents of two stacks.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::stack<int> stk1 = {1, 2, 3};
std::stack<int> stk2 = {4, 5, 6};
stk1.swap(stk2);  // Swaps the contents of stk1 and stk2
```

<br>

---

<br>

## Non-Member Functions

<br>

### operator==

**Description:** Compares two stacks for equality.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

### std::swap

**Description:** Specializes `std::swap` for stacks.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |