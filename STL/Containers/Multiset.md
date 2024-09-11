
`std::multiset` is an associative container that contains a sorted set of elements, where multiple elements can have the same value. Unlike `std::set`, `std::multiset` allows duplicates. It automatically sorts the elements in ascending order (by default). Internally, it is typically implemented as a self-balancing binary search tree.

<br>

---

<br>

## Time and Space Complexity Summary

<br>

| Operation            | Time Complexity | Space Complexity |
|----------------------|-----------------|------------------|
| Access (find)        | $O(\log n)$     | $O(1)$           |
| Insert               | $O(\log n)$     | $O(n)$           |
| Erase (single)       | $O(\log n)$     | $O(n)$           |
| Erase (range)        | $O(k + \log n)$ | $O(n)$           |
| Size                 | $O(1)$          | $O(1)$           |
| Clear                | $O(n)$          | $O(1)$           |
| Traverse             | $O(n)$          | $O(n)$           |

<br>

---

<br>

## Setup

<br>

The `<set>` library header is required.

```cpp
#include <set>
```

<br>

---

<br>

## Declaration

<br>

Create an empty multiset:

```cpp
std::multiset<int> ms;
```

<br>

Create a multiset with elements 1, 2, and 3:

```cpp
std::multiset<int> ms = {1, 2, 3};
```

<br>

Create a multiset with a custom comparator (descending order):

```cpp
auto cmp = [](int a, int b) { return a > b; };
std::multiset<int, decltype(cmp)> ms(cmp); // Multiset with custom comparator
```

<br>

---

<br>

## Insertion and Deletion

<br>

#### `insert`

- **Description:** Inserts an element into the multiset.
- **Complexity:** $O(\log n)$

```cpp
ms.insert(5); // Adds 5 to the multiset
```

Multiple duplicate elements can be added:

```cpp
ms.insert(5); // Adds another 5 to the multiset
```

<br>

#### `emplace`

- **Description:** Constructs and inserts an element into the multiset in-place.
- **Complexity:** $O(\log n)$

```cpp
ms.emplace(10); // Constructs and adds 10 to the multiset
```

<br>

#### `erase`

- **Description:** Removes the element(s) matching the given key or position.
- **Complexity:** $O(\log n)$

```cpp
ms.erase(5); // Removes all elements with key 5
```

- **Erase by iterator:**

```cpp
auto it = ms.find(10);
if (it != ms.end()) {
    ms.erase(it); // Removes a single occurrence of the element 10
}
```

- **Erase by range:**

```cpp
ms.erase(ms.begin(), ms.end()); // Removes all elements
```

<br>

#### `clear`

- **Description:** Removes all elements from the multiset.
- **Complexity:** $O(n)$

```cpp
ms.clear(); // Removes all elements from the multiset
```

<br>

---

<br>

## Element Access

<br>

#### `find`

- **Description:** Searches for the first occurrence of the element with the given key.
- **Complexity:** $O(\log n)$

```cpp
auto it = ms.find(5); // Searches for 5 in the multiset
if (it != ms.end()) {
    std::cout << "Found 5";
}
```

<br>

#### `count`

- **Description:** Returns the number of elements that match the given key.
- **Complexity:** $O(\log n)$

```cpp
std::size_t cnt = ms.count(5); // Returns the number of occurrences of 5
```

<br>

#### `lower_bound`

- **Description:** Returns an iterator to the first element that is not less than the given key.
- **Complexity:** $O(\log n)$

```cpp
auto it = ms.lower_bound(5); // Iterator to the first element >= 5
```

<br>

#### `upper_bound`

- **Description:** Returns an iterator to the first element that is greater than the given key.
- **Complexity:** $O(\log n)$

```cpp
auto it = ms.upper_bound(5); // Iterator to the first element > 5
```

<br>

#### `equal_range`

- **Description:** Returns a pair of iterators that represents the range of elements that are equal to the given key.
- **Complexity:** $O(\log n)$

```cpp
auto range = ms.equal_range(5); // Returns pair of iterators to elements equal to 5
```

<br>

---

<br>

## Size Operations

<br>

#### `size`

- **Description:** Returns the number of elements in the multiset.
- **Complexity:** $O(1)$

```cpp
std::size_t sz = ms.size(); // Get the number of elements
```

<br>

#### `empty`

- **Description:** Checks if the multiset is empty.
- **Complexity:** $O(1)$

```cpp
bool isEmpty = ms.empty(); // Returns true if the multiset is empty
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
for (auto it = ms.begin(); it != ms.end(); ++it) {
    std::cout << *it << " ";
}
```

<br>

---

<br>

## Other Operations

<br>

#### `swap`

- **Description:** Swaps the content of two multisets.
- **Complexity:** $O(1)$

```cpp
std::multiset<int> ms2 = {9, 8, 7};
ms.swap(ms2); // Swaps content of ms and ms2
```

<br>

#### `assign`

- **Description:** Assigns new values to the multiset, replacing the old ones.
- **Complexity:** $O(n \log n)$

```cpp
ms = {5, 6, 7, 8}; // Assigns new values to the multiset
```

<br>

---

<br>

## Set Operations

<br>

#### `merge`

- **Description:** Merges two multisets (the source multiset is not emptied).
- **Complexity:** $O(n \log n)$

```cpp
std::multiset<int> ms2 = {1, 4, 6};
ms.merge(ms2); // Merges ms2 into ms, ms2 retains its elements
```

<br>

#### `equal_range`

- **Description:** Returns a range of elements that are equal to the given key.
- **Complexity:** $O(\log n)$

```cpp
auto range = ms.equal_range(5); // Returns a pair of iterators for range of elements == 5
```

<br>

---

<br>

## Custom Comparators

<br>

#### Example of a custom comparator (Descending order):

```cpp
auto cmp = [](int a, int b) { return a > b; };
std::multiset<int, decltype(cmp)> ms(cmp);
```

<br>

In this example, the multiset will store the elements in descending order instead of the default ascending order.

<br>

---

<br>

## Special Properties of `std::multiset`

<br>

- Unlike `std::set`, `std::multiset` allows duplicate elements.
- Elements are stored in a specific order (ascending by default).
- Efficient insertion, deletion, and lookup with $O(\log n)$ complexity.
