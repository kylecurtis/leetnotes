
`std::list` is a doubly-linked list that allows efficient insertion and deletion of elements from both the front and back. Unlike `std::vector` and `std::deque`, accessing elements by index is not constant time since `std::list` does not provide random access. It is best suited for use cases where frequent insertions or deletions are required in the middle of a sequence.

<br>

---

<br>

## Time and Space Complexity Summary

<br>

| Operation         | Time Complexity | Space Complexity |
|-------------------|-----------------|------------------|
| Access (front/back) | $O(1)$         | $O(1)$           |
| Access (middle)    | $O(n)$          | $O(n)$           |
| Insert (front/back)| $O(1)$          | $O(1)$           |
| Insert (middle)    | $O(1)$ for insertion, traversal $O(n)$ | $O(1)$ |
| Erase (front/back) | $O(1)$          | $O(n)$           |
| Erase (middle)     | $O(1)$ for erasure, traversal $O(n)$ | $O(n)$ |
| Push Front         | $O(1)$          | $O(1)$           |
| Push Back          | $O(1)$          | $O(1)$           |
| Pop Front          | $O(1)$          | $O(1)$           |
| Pop Back           | $O(1)$          | $O(1)$           |
| Size               | $O(1)$          | $O(1)$           |
| Clear              | $O(n)$          | $O(1)$           |

<br>

---

<br>

## Setup

<br>

The `<list>` library header is required.

```cpp
#include <list>
```

<br>

---

<br>

## Declaration

<br>

Create an empty list:

```cpp
std::list<int> lst;
```

<br>

Create a list with 10 default-initialized elements:

```cpp
std::list<int> lst(10);
```

<br>

Create a list with 10 elements, each initialized to 5:

```cpp
std::list<int> lst(10, 5);
```

<br>

Create a list with elements 1, 2, and 3:

```cpp
std::list<int> lst = {1, 2, 3};
```

<br>

---

<br>

## Insertion and Deletion

<br>

#### `push_back`

- **Description:** Inserts an element at the end of the list.
- **Complexity:** $O(1)$

```cpp
lst.push_back(5); // Adds 5 to the end of the list
```

<br>

#### `push_front`

- **Description:** Inserts an element at the front of the list.
- **Complexity:** $O(1)$

```cpp
lst.push_front(10); // Adds 10 to the front of the list
```

<br>

#### `emplace_back`

- **Description:** Constructs and inserts an element at the back of the list.
- **Complexity:** $O(1)$

```cpp
lst.emplace_back(15); // Constructs and adds 15 to the end of the list
```

<br>

#### `emplace_front`

- **Description:** Constructs and inserts an element at the front of the list.
- **Complexity:** $O(1)$

```cpp
lst.emplace_front(20); // Constructs and adds 20 to the front of the list
```

<br>

#### `insert`

- **Description:** Inserts one or more elements before the given position.
- **Complexity:** $O(1)$ for insertion, traversal $O(n)$

```cpp
auto it = lst.begin();
std::advance(it, 1);
lst.insert(it, 100); // Inserts 100 at position 1
lst.insert(lst.begin(), {4, 5, 6}); // Inserts multiple elements at the beginning
```

<br>

#### `pop_back`

- **Description:** Removes the last element from the list.
- **Complexity:** $O(1)$

```cpp
lst.pop_back(); // Removes the last element
```

<br>

#### `pop_front`

- **Description:** Removes the first element from the list.
- **Complexity:** $O(1)$

```cpp
lst.pop_front(); // Removes the first element
```

<br>

#### `erase`

- **Description:** Removes an element or a range of elements.
- **Complexity:** $O(1)$ for erasure, traversal $O(n)$

```cpp
auto it = lst.begin();
std::advance(it, 2);
lst.erase(it); // Removes the element at position 2
lst.erase(lst.begin(), std::next(lst.begin(), 2)); // Removes elements in the range [begin, begin + 2)
```

<br>

#### `clear`

- **Description:** Removes all elements.
- **Complexity:** $O(n)$

```cpp
lst.clear(); // Removes all elements from the list
```

<br>

---

<br>

## Element Access

<br>

#### `front` and `back`

- **Description:** Accesses the first or last element of the list.
- **Complexity:** $O(1)$

```cpp
int first = lst.front(); // Access the first element
int last = lst.back(); // Access the last element
```

<br>

---

<br>

## Size Operations

<br>

#### `size`

- **Description:** Returns the number of elements in the list.
- **Complexity:** $O(1)$

```cpp
std::size_t sz = lst.size(); // Get the number of elements
```

<br>

#### `empty`

- **Description:** Checks if the list is empty.
- **Complexity:** $O(1)$

```cpp
bool isEmpty = lst.empty(); // Returns true if the list is empty
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
for (auto it = lst.begin(); it != lst.end(); ++it) {
    std::cout << *it << " ";
}

for (auto rit = lst.rbegin(); rit != lst.rend(); ++rit) {
    std::cout << *rit << " ";
}
```

<br>

---

<br>

## Other Operations

<br>

#### `swap`

- **Description:** Swaps the content of two lists.
- **Complexity:** $O(1)$

```cpp
std::list<int> lst2 = {9, 8, 7};
lst.swap(lst2); // Swaps content of lst and lst2
```

<br>

#### `assign`

- **Description:** Assigns new values to the list, replacing the old ones.
- **Complexity:** $O(n)$

```cpp
lst.assign(5, 100); // Assigns 5 elements with the value 100
lst.assign({1, 2, 3, 4}); // Assigns initializer list
```

<br>

---

<br>

## Splice Operations

<br>

#### `splice`

- **Description:** Transfers elements from one list to another.
- **Complexity:** $O(1)$ for splice, $O(n)$ traversal if necessary.

```cpp
std::list<int> lst2 = {50, 60, 70};
lst.splice(lst.begin(), lst2); // Transfers all elements from lst2 to the front of lst
```

<br>

---

<br>

## Sorting and Merging

<br>

#### `sort`

- **Description:** Sorts the elements in ascending order.
- **Complexity:** $O(n \log n)$

```cpp
lst.sort(); // Sorts the list in ascending order
```

<br>

#### `merge`

- **Description:** Merges two sorted lists into one sorted list.
- **Complexity:** $O(n)$

```cpp
std::list<int> lst2 = {1, 3, 5};
lst.merge(lst2); // Merges lst2 into lst
```
