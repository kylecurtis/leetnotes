
`std::forward_list` is a singly linked list. It is similar to `std::list`, but only supports forward traversal (no reverse iterators). The `std::forward_list` uses less memory compared to `std::list` due to its simple structure but lacks the ability to traverse in reverse or access elements at both ends efficiently.

<br>

---

<br>

## Time and Space Complexity Summary

<br>

| Operation           | Time Complexity | Space Complexity |
|---------------------|-----------------|------------------|
| Access (front)       | $O(1)$          | $O(1)$           |
| Access (middle)      | $O(n)$          | $O(n)$           |
| Insert (front)       | $O(1)$          | $O(1)$           |
| Insert (middle)      | $O(1)$ for insertion, traversal $O(n)$ | $O(1)$ |
| Erase (front)        | $O(1)$          | $O(n)$           |
| Erase (middle)       | $O(1)$ for erasure, traversal $O(n)$ | $O(n)$ |
| Push Front           | $O(1)$          | $O(1)$           |
| Pop Front            | $O(1)$          | $O(1)$           |
| Size                 | $O(n)$          | $O(1)$           |
| Clear                | $O(n)$          | $O(1)$           |

<br>

---

<br>

## Setup

<br>

The `<forward_list>` library header is required.

```cpp
#include <forward_list>
```

<br>

---

<br>

## Declaration

<br>

Create an empty forward list:

```cpp
std::forward_list<int> fwd_lst;
```

<br>

Create a forward list with 10 default-initialized elements:

```cpp
std::forward_list<int> fwd_lst(10);
```

<br>

Create a forward list with 10 elements, each initialized to 5:

```cpp
std::forward_list<int> fwd_lst(10, 5);
```

<br>

Create a forward list with elements 1, 2, and 3:

```cpp
std::forward_list<int> fwd_lst = {1, 2, 3};
```

<br>

---

<br>

## Insertion and Deletion

<br>

#### `push_front`

- **Description:** Inserts an element at the front of the forward list.
- **Complexity:** $O(1)$

```cpp
fwd_lst.push_front(10); // Adds 10 to the front of the forward list
```

<br>

#### `emplace_front`

- **Description:** Constructs and inserts an element at the front of the forward list.
- **Complexity:** $O(1)$

```cpp
fwd_lst.emplace_front(20); // Constructs and adds 20 to the front of the forward list
```

<br>

#### `insert_after`

- **Description:** Inserts one or more elements after the given position.
- **Complexity:** $O(1)$ for insertion, traversal $O(n)$

```cpp
auto it = fwd_lst.begin();
fwd_lst.insert_after(it, 100); // Inserts 100 after the first element
fwd_lst.insert_after(it, {4, 5, 6}); // Inserts multiple elements after the first element
```

<br>

#### `erase_after`

- **Description:** Removes an element or a range of elements after the given position.
- **Complexity:** $O(1)$ for erasure, traversal $O(n)$

```cpp
auto it = fwd_lst.begin();
fwd_lst.erase_after(it); // Removes the element after the first element
fwd_lst.erase_after(it, std::next(it, 3)); // Removes elements in the range [it, it + 3)
```

<br>

#### `pop_front`

- **Description:** Removes the first element from the forward list.
- **Complexity:** $O(1)$

```cpp
fwd_lst.pop_front(); // Removes the first element
```

<br>

#### `clear`

- **Description:** Removes all elements.
- **Complexity:** $O(n)$

```cpp
fwd_lst.clear(); // Removes all elements from the forward list
```

<br>

---

<br>

## Element Access

<br>

#### `front`

- **Description:** Accesses the first element of the forward list.
- **Complexity:** $O(1)$

```cpp
int first = fwd_lst.front(); // Access the first element
```

<br>

---

<br>

## Size Operations

<br>

Note that `std::forward_list` does **not** provide a `size()` function since it is a singly linked list and calculating size requires traversing the entire list. You must manually track the size or calculate it on demand.

<br>

#### Size Calculation Example:

```cpp
std::size_t size = std::distance(fwd_lst.begin(), fwd_lst.end()); // Calculate size manually
```

<br>

#### `empty`

- **Description:** Checks if the forward list is empty.
- **Complexity:** $O(1)$

```cpp
bool isEmpty = fwd_lst.empty(); // Returns true if the forward list is empty
```

<br>

---

<br>

## Iterators

<br>

#### `begin`, `end`

- **Description:** Provides iterators for range-based loops and algorithms.
- **Complexity:** $O(1)$

```cpp
for (auto it = fwd_lst.begin(); it != fwd_lst.end(); ++it) {
    std::cout << *it << " ";
}
```

<br>

---

<br>

## Other Operations

<br>

#### `swap`

- **Description:** Swaps the content of two forward lists.
- **Complexity:** $O(1)$

```cpp
std::forward_list<int> fwd_lst2 = {9, 8, 7};
fwd_lst.swap(fwd_lst2); // Swaps content of fwd_lst and fwd_lst2
```

<br>

#### `assign`

- **Description:** Assigns new values to the forward list, replacing the old ones.
- **Complexity:** $O(n)$

```cpp
fwd_lst.assign(5, 100); // Assigns 5 elements with the value 100
fwd_lst.assign({1, 2, 3, 4}); // Assigns initializer list
```

<br>

---

<br>

## Splice Operations

<br>

#### `splice_after`

- **Description:** Transfers elements from one forward list to another after the given position.
- **Complexity:** $O(1)$ for splice, traversal $O(n)$

```cpp
std::forward_list<int> fwd_lst2 = {50, 60, 70};
fwd_lst.splice_after(fwd_lst.begin(), fwd_lst2); // Transfers all elements from fwd_lst2 to fwd_lst after the first element
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
fwd_lst.sort(); // Sorts the forward list in ascending order
```

<br>

#### `merge`

- **Description:** Merges two sorted forward lists into one sorted forward list.
- **Complexity:** $O(n)$

```cpp
std::forward_list<int> fwd_lst2 = {1, 3, 5};
fwd_lst.merge(fwd_lst2); // Merges fwd_lst2 into fwd_lst
```
