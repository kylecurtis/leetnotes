
`std::set` is an associative container that contains a sorted set of unique objects. It automatically sorts the elements in ascending order (by default) and ensures that all the elements are unique. Internally, it is usually implemented as a self-balancing binary search tree (e.g., Red-Black Tree).

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

Create an empty set:

```cpp
std::set<int> s;
```

<br>

Create a set with elements 1, 2, and 3:

```cpp
std::set<int> s = {1, 2, 3};
```

<br>

Create a set with a custom comparator (descending order):

```cpp
auto cmp = [](int a, int b) { return a > b; };
std::set<int, decltype(cmp)> s(cmp); // Set with custom comparator
```

<br>

---

<br>

## Insertion and Deletion

<br>

#### `insert`

- **Description:** Inserts an element into the set if it is not already present.
- **Complexity:** $O(\log n)$

```cpp
s.insert(5); // Adds 5 to the set if it's not already present
```

<br>

#### `emplace`

- **Description:** Constructs and inserts an element into the set in-place.
- **Complexity:** $O(\log n)$

```cpp
s.emplace(10); // Constructs and adds 10 to the set if it's not already present
```

<br>

#### `erase`

- **Description:** Removes the element at the specified position or key.
- **Complexity:** $O(\log n)$

```cpp
s.erase(5); // Removes the element with key 5
```

- **Erase by iterator:**

```cpp
auto it = s.find(10);
if (it != s.end()) {
    s.erase(it); // Removes the element pointed to by the iterator
}
```

- **Erase by range:**

```cpp
s.erase(s.begin(), s.end()); // Removes all elements
```

<br>

#### `clear`

- **Description:** Removes all elements from the set.
- **Complexity:** $O(n)$

```cpp
s.clear(); // Removes all elements from the set
```

<br>

---

<br>

## Element Access

<br>

#### `find`

- **Description:** Searches for the element with the given key.
- **Complexity:** $O(\log n)$

```cpp
auto it = s.find(5); // Searches for 5 in the set
if (it != s.end()) {
    std::cout << "Found 5";
}
```

<br>

#### `count`

- **Description:** Returns the number of elements matching the given key (in a set, it’s always 0 or 1).
- **Complexity:** $O(\log n)$

```cpp
if (s.count(5)) {
    std::cout << "5 exists in the set";
}
```

<br>

#### `lower_bound`

- **Description:** Returns an iterator to the first element that is not less than the given key.
- **Complexity:** $O(\log n)$

```cpp
auto it = s.lower_bound(5); // Iterator to the first element >= 5
```

<br>

#### `upper_bound`

- **Description:** Returns an iterator to the first element that is greater than the given key.
- **Complexity:** $O(\log n)$

```cpp
auto it = s.upper_bound(5); // Iterator to the first element > 5
```

<br>

---

<br>

## Size Operations

<br>

#### `size`

- **Description:** Returns the number of elements in the set.
- **Complexity:** $O(1)$

```cpp
std::size_t sz = s.size(); // Get the number of elements
```

<br>

#### `empty`

- **Description:** Checks if the set is empty.
- **Complexity:** $O(1)$

```cpp
bool isEmpty = s.empty(); // Returns true if the set is empty
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
for (auto it = s.begin(); it != s.end(); ++it) {
    std::cout << *it << " ";
}
```

<br>

---

<br>

## Other Operations

<br>

#### `swap`

- **Description:** Swaps the content of two sets.
- **Complexity:** $O(1)$

```cpp
std::set<int> s2 = {9, 8, 7};
s.swap(s2); // Swaps content of s and s2
```

<br>

#### `assign`

- **Description:** Assigns new values to the set, replacing the old ones.
- **Complexity:** $O(n \log n)$

```cpp
s = {5, 6, 7, 8}; // Assigns new values to the set
```

<br>

---

<br>

## Set Operations

<br>

#### `merge`

- **Description:** Merges two sets (the source set is emptied).
- **Complexity:** $O(n \log n)$

```cpp
std::set<int> s2 = {1, 4, 6};
s.merge(s2); // Merges s2 into s, s2 is emptied
```

<br>

#### `equal_range`

- **Description:** Returns a range of elements that are equal to the given key (for `std::set`, this will return either a single element or an empty range since duplicates are not allowed).
- **Complexity:** $O(\log n)$

```cpp
auto range = s.equal_range(5); // Returns a pair of iterators for range of elements == 5
```

<br>

---

<br>

## Custom Comparators

<br>

#### Example of a custom comparator (Descending order):

```cpp
auto cmp = [](int a, int b) { return a > b; };
std::set<int, decltype(cmp)> s(cmp);
```

<br>

In this example, the set will store the elements in descending order instead of the default ascending order.

<br>

---

<br>

## Special Properties of `std::set`

<br>

- All elements in `std::set` are unique.
- Elements are stored in a specific order (ascending by default).
- Efficient insertion, deletion, and lookup with $O(\log n)$ complexity.