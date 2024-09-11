
`std::deque` is a double-ended queue that allows fast insertions and deletions at both ends (front and back). It provides random access and behaves similarly to `std::vector`, but with more flexibility regarding insertion and deletion at the front.

<br>

---

<br>

## Time and Space Complexity Summary

<br>

| Operation         | Time Complexity | Space Complexity |
|-------------------|-----------------|------------------|
| Access (at, [])   | $O(1)$          | $O(1)$           |
| Insert (front)    | $O(1)$          | $O(n)$ (if reallocation) |
| Insert (back)     | $O(1)$          | $O(n)$ (if reallocation) |
| Insert (middle)   | $O(n)$          | $O(n)$           |
| Erase (front)     | $O(1)$          | $O(n)$           |
| Erase (back)      | $O(1)$          | $O(n)$           |
| Erase (middle)    | $O(n)$          | $O(n)$           |
| Push Front        | $O(1)$          | $O(n)$ (if reallocation) |
| Push Back         | $O(1)$          | $O(n)$ (if reallocation) |
| Pop Front         | $O(1)$          | $O(1)$           |
| Pop Back          | $O(1)$          | $O(1)$           |
| Size              | $O(1)$          | $O(1)$           |
| Clear             | $O(n)$          | $O(1)$           |
| Reserve           | N/A             | N/A              |
| Resize            | $O(n)$          | $O(n)$           |

<br>

---

<br>

## Setup

<br>

The `<deque>` library header is required.

```cpp
#include <deque>
```

<br>

---

<br>

## Declaration

<br>

Create an empty deque:

```cpp
std::deque<int> deq;
```

<br>

Create a deque with 10 default-initialized elements:

```cpp
std::deque<int> deq(10);
```

<br>

Create a deque with 10 elements, each initialized to 5:

```cpp
std::deque<int> deq(10, 5);
```

<br>

Create a deque with elements 1, 2, and 3:

```cpp
std::deque<int> deq = {1, 2, 3};
```

<br>

---

<br>

## Insertion and Deletion

<br>

#### `push_back`

- **Description:** Inserts an element at the back of the deque.
- **Complexity:** $O(1)$

```cpp
deq.push_back(5); // Adds 5 to the end of the deque
```

<br>

#### `push_front`

- **Description:** Inserts an element at the front of the deque.
- **Complexity:** $O(1)$

```cpp
deq.push_front(10); // Adds 10 to the front of the deque
```

<br>

#### `emplace_back`

- **Description:** Constructs and inserts an element at the back of the deque.
- **Complexity:** $O(1)$

```cpp
deq.emplace_back(15); // Constructs and adds 15 to the end of the deque
```

<br>

#### `emplace_front`

- **Description:** Constructs and inserts an element at the front of the deque.
- **Complexity:** $O(1)$

```cpp
deq.emplace_front(20); // Constructs and adds 20 to the front of the deque
```

<br>

#### `insert`

- **Description:** Inserts one or more elements before the given position.
- **Complexity:** $O(n)$

```cpp
deq.insert(deq.begin() + 1, 100); // Inserts 100 at position 1
deq.insert(deq.begin(), {4, 5, 6}); // Inserts multiple elements at the beginning
```

<br>

#### `pop_back`

- **Description:** Removes the last element from the deque.
- **Complexity:** $O(1)$

```cpp
deq.pop_back(); // Removes the last element
```

<br>

#### `pop_front`

- **Description:** Removes the first element from the deque.
- **Complexity:** $O(1)$

```cpp
deq.pop_front(); // Removes the first element
```

<br>

#### `erase`

- **Description:** Removes an element or a range of elements.
- **Complexity:** $O(n)$

```cpp
deq.erase(deq.begin() + 2); // Removes the element at position 2
deq.erase(deq.begin(), deq.begin() + 2); // Removes elements in the range [begin, begin + 2)
```

<br>

#### `clear`

- **Description:** Removes all elements.
- **Complexity:** $O(n)$

```cpp
deq.clear(); // Removes all elements from the deque
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
int x = deq[0]; // Access the first element (no bounds checking)
int y = deq.at(2); // Access the third element (with bounds checking)
```

<br>

#### `front` and `back`

- **Description:** Accesses the first or last element of the deque.
- **Complexity:** $O(1)$

```cpp
int first = deq.front(); // Access the first element
int last = deq.back(); // Access the last element
```

<br>

---

<br>

## Size Operations

<br>

#### `size`

- **Description:** Returns the number of elements in the deque.
- **Complexity:** $O(1)$

```cpp
std::size_t sz = deq.size(); // Get the number of elements
```

<br>

#### `empty`

- **Description:** Checks if the deque is empty.
- **Complexity:** $O(1)$

```cpp
bool isEmpty = deq.empty(); // Returns true if the deque is empty
```

<br>

---

<br>

## Resizing and Shrinking

<br>

#### `resize`

- **Description:** Changes the size of the deque.
- **Complexity:** $O(n)$

```cpp
deq.resize(20); // Resize the deque to hold 20 elements
deq.resize(5); // Shrink the deque to 5 elements
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
for (auto it = deq.begin(); it != deq.end(); ++it) {
    std::cout << *it << " ";
}

for (auto rit = deq.rbegin(); rit != deq.rend(); ++rit) {
    std::cout << *rit << " ";
}
```

<br>

---

<br>

## Other Operations

<br>

#### `swap`

- **Description:** Swaps the content of two deques.
- **Complexity:** $O(1)$

```cpp
std::deque<int> deq2 = {9, 8, 7};
deq.swap(deq2); // Swaps content of deq and deq2
```

<br>

#### `assign`

- **Description:** Assigns new values to the deque, replacing the old ones.
- **Complexity:** $O(n)$

```cpp
deq.assign(5, 100); // Assigns 5 elements with the value 100
deq.assign({1, 2, 3, 4}); // Assigns initializer list
```
