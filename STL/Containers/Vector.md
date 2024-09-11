
`std::vector` is a dynamic array that provides random access, constant time for element access, and amortized constant time for insertion at the end. It is the most commonly used sequence container in C++.

<br>

---

<br>

## Time and Space Complexity Summary

<br>

| Operation         | Time Complexity | Space Complexity |
|-------------------|-----------------|------------------|
| Access (at, [])   | $O(1)$            | $O(1)$             |
| Insert (end)      | Amortized $O(1)$  | $O(n)$ (if reallocation) |
| Insert (middle)   | $O(n)$           | $O(n)$             |
| Erase (end)       | $O(1)$            | $O(n)$             |
| Erase (middle)    | $O(n)$            | $O(n)$            |
| Push Back         | Amortized $O(1)$  | $O(n)$ (if reallocation) |
| Pop Back          | $O(1)$            | $O(1)$             |
| Size              | $O(1)$           | $O(1)$             |
| Clear             | $O(n)$            | $O(1)$             |
| Reserve           | $O(n)$            | $O(n)$             |
| Resize            | $O(n)$            | $O(n)$             |

<br>

---

<br>

## Setup

<br>

The `<vector>` library header is required.

```cpp
#include <vector>
```

<br>

---

<br>

## Declaration

<br>

Create an empty vector:

```cpp
std::vector<int> vec;
```

<br>

Create a vector with 10 default-initialized elements:

```cpp
std::vector<int> vec(10);
```

<br>

Create a vector with 10 elements, each initialized to 5:

```cpp
std::vector<int> vec(10, 5);
```

<br>

Create a vector with elements 1, 2, and 3:

```cpp
std::vector<int> vec = {1, 2, 3};
```

<br>

---

<br>

## Insertion and Deletion

<br>

#### `push_back`

- **Description:** Inserts an element at the end of the vector.
- **Complexity:** Amortized $O(1)$, worst case $O(n)$ when reallocation happens.
  
```cpp
vec.push_back(5); // Adds 5 to the end of the vector
```

<br>

#### `emplace_back`

- **Description:** Constructs and inserts an element at the end of the vector.
- **Complexity:** Amortized $O(1)$, worst case $O(n)$ when reallocation happens.

```cpp
vec.emplace_back(10); // More efficient than push_back for complex objects
```

<br>

#### `insert`

- **Description:** Inserts one or more elements before the given position.
- **Complexity:** $O(n)$ in the worst case.

```cpp
vec.insert(vec.begin() + 1, 100); // Inserts 100 at position 1
vec.insert(vec.begin(), {4, 5, 6}); // Inserts multiple elements at the beginning
```

<br>

#### `pop_back`

- **Description:** Removes the last element from the vector.
- **Complexity:** $O(1)$

```cpp
vec.pop_back(); // Removes the last element
```

<br>

#### `erase`

- **Description:** Removes an element or a range of elements.
- **Complexity:** $O(n)$ for range erasing.

```cpp
vec.erase(vec.begin() + 2); // Removes the element at position 2
vec.erase(vec.begin(), vec.begin() + 2); // Removes elements in the range [begin, begin + 2)
```

<br>

#### `clear`

- **Description:** Removes all elements.
- **Complexity:** $O(n)$

```cpp
vec.clear(); // Removes all elements from the vector
```

<br>

---

<br>

## Element Access

<br>

#### `operator[]` and `at`

- **Description:** Accesses an element at the given position.
- **Complexity:** $O(1)$

```cpp
int x = vec[0]; // Access the first element (no bounds checking)
int y = vec.at(2); // Access the third element (with bounds checking)
```

<br>

#### `front` and `back`

- **Description:** Accesses the first or last element of the vector.
- **Complexity:** $O(1)$

```cpp
int first = vec.front(); // Access the first element
int last = vec.back(); // Access the last element
```

<br>

---

<br>

## Size Operations

<br>

#### `size`

- **Description:** Returns the number of elements in the vector.
- **Complexity:** $O(1)$

```cpp
std::size_t sz = vec.size(); // Get the number of elements
```

<br>

#### `empty`

- **Description:** Checks if the vector is empty.
- **Complexity:** $O(1)$

```cpp
bool isEmpty = vec.empty(); // Returns true if the vector is empty
```

<br>

#### `capacity` and `reserve`

- **Description:** `capacity` returns the number of elements that can be held without reallocation. `reserve` requests capacity change.
- **Complexity:** $O(1)$ for `capacity`, $O(n)$ for `reserve` in the worst case.

```cpp
std::size_t cap = vec.capacity(); // Get current capacity
vec.reserve(50); // Reserve capacity for 50 elements
```

<br>

---

<br>

## Resizing and Shrinking

<br>

#### `resize`

- **Description:** Changes the size of the vector.
- **Complexity:** $O(n)$

```cpp
vec.resize(20); // Resize the vector to hold 20 elements
vec.resize(5); // Shrink the vector to 5 elements
```

<br>

#### `shrink_to_fit`

- **Description:** Reduces the capacity of the vector to fit its size.
- **Complexity:** $O(n)$

```cpp
vec.shrink_to_fit(); // Shrinks capacity to fit the current size
```

<br>

---

<br>

## Iterators

<br>

#### `begin`, `end`, `rbegin`, `rend`

- **Description:** Provides iterators for range-based loops and algorithms.
- **Complexity:** $O(1)$

```cpp
for (auto it = vec.begin(); it != vec.end(); ++it) {
    std::cout << *it << " ";
}

for (auto rit = vec.rbegin(); rit != vec.rend(); ++rit) {
    std::cout << *rit << " ";
}
```

<br>

---

<br>

## Other Operations

#### `swap`

- **Description:** Swaps the content of two vectors.
- **Complexity:** $O(1)$

```cpp
std::vector<int> vec2 = {9, 8, 7};
vec.swap(vec2); // Swaps content of vec and vec2
```

<br>

#### `assign`

- **Description:** Assigns new values to the vector, replacing the old ones.
- **Complexity:** $O(n)$

```cpp
vec.assign(5, 100); // Assigns 5 elements with the value 100
vec.assign({1, 2, 3, 4}); // Assigns initializer list
```
