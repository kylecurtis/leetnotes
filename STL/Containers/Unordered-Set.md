
`std::unordered_set` is an associative container that contains a unique set of elements. Unlike `std::set`, elements in `std::unordered_set` are not sorted; instead, they are organized into buckets using a hash function. This provides average constant-time complexity ($O(1)$) for insertion, deletion, and lookup, but performance can degrade to $O(n)$ in the worst case (due to hash collisions).

<br>

---

<br>

## Time and Space Complexity Summary

<br>

| Operation            | Average Time Complexity | Worst Case Time Complexity | Space Complexity |
|----------------------|-------------------------|----------------------------|------------------|
| Access (find)        | $O(1)$                  | $O(n)$                     | $O(1)$           |
| Insert               | $O(1)$                  | $O(n)$                     | $O(n)$           |
| Erase (single)       | $O(1)$                  | $O(n)$                     | $O(n)$           |
| Size                 | $O(1)$                  | $O(1)$                     | $O(1)$           |
| Clear                | $O(n)$                  | $O(n)$                     | $O(1)$           |
| Traverse             | $O(n)$                  | $O(n)$                     | $O(n)$           |

<br>

---

<br>

## Setup

<br>

The `<unordered_set>` library header is required.

```cpp
#include <unordered_set>
```

<br>

---

<br>

## Declaration

<br>

Create an empty unordered set:

```cpp
std::unordered_set<int> us;
```

<br>

Create an unordered set with elements 1, 2, and 3:

```cpp
std::unordered_set<int> us = {1, 2, 3};
```

<br>

Create an unordered set with a custom hash function:

```cpp
auto hashFunc = [](int x) { return x % 10; };
std::unordered_set<int, decltype(hashFunc)> us(10, hashFunc); // Unordered set with custom hash function
```

<br>

---

<br>

## Insertion and Deletion

<br>

#### `insert`

- **Description:** Inserts an element into the unordered set if it is not already present.
- **Complexity:** Average $O(1)$, worst case $O(n)$

```cpp
us.insert(5); // Adds 5 to the unordered set if it's not already present
```

<br>

#### `emplace`

- **Description:** Constructs and inserts an element into the unordered set in-place.
- **Complexity:** Average $O(1)$, worst case $O(n)$

```cpp
us.emplace(10); // Constructs and adds 10 to the unordered set
```

<br>

#### `erase`

- **Description:** Removes the element with the given key.
- **Complexity:** Average $O(1)$, worst case $O(n)$

```cpp
us.erase(5); // Removes the element with key 5
```

- **Erase by iterator:**

```cpp
auto it = us.find(10);
if (it != us.end()) {
    us.erase(it); // Removes the element pointed to by the iterator
}
```

<br>

#### `clear`

- **Description:** Removes all elements from the unordered set.
- **Complexity:** $O(n)$

```cpp
us.clear(); // Removes all elements from the unordered set
```

<br>

---

<br>

## Element Access

<br>

#### `find`

- **Description:** Searches for the element with the given key.
- **Complexity:** Average $O(1)$, worst case $O(n)$

```cpp
auto it = us.find(5); // Searches for 5 in the unordered set
if (it != us.end()) {
    std::cout << "Found 5";
}
```

<br>

#### `count`

- **Description:** Returns the number of elements matching the given key (in an unordered set, it’s always 0 or 1).
- **Complexity:** Average $O(1)$, worst case $O(n)$

```cpp
if (us.count(5)) {
    std::cout << "5 exists in the unordered set";
}
```

<br>

---

<br>

## Size Operations

<br>

#### `size`

- **Description:** Returns the number of elements in the unordered set.
- **Complexity:** $O(1)$

```cpp
std::size_t sz = us.size(); // Get the number of elements
```

<br>

#### `empty`

- **Description:** Checks if the unordered set is empty.
- **Complexity:** $O(1)$

```cpp
bool isEmpty = us.empty(); // Returns true if the unordered set is empty
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
for (auto it = us.begin(); it != us.end(); ++it) {
    std::cout << *it << " ";
}
```

<br>

---

<br>

## Bucket Interface

`std::unordered_set` stores elements in buckets and uses hash functions to determine the bucket for each element. The bucket interface provides methods to query these buckets.

<br>

#### `bucket_count`

- **Description:** Returns the number of buckets used by the unordered set.
- **Complexity:** $O(1)$

```cpp
std::size_t bucketCount = us.bucket_count(); // Get the number of buckets
```

<br>

#### `bucket`

- **Description:** Returns the bucket index for a given key.
- **Complexity:** $O(1)$

```cpp
std::size_t bucketIndex = us.bucket(5); // Get the bucket index for the element 5
```

<br>

#### `load_factor`

- **Description:** Returns the average number of elements per bucket.
- **Complexity:** $O(1)$

```cpp
float loadFactor = us.load_factor(); // Get the load factor
```

<br>

#### `max_load_factor`

- **Description:** Returns or sets the maximum load factor, which is used to determine when the container should increase the number of buckets.
- **Complexity:** $O(1)$

```cpp
us.max_load_factor(1.0); // Sets the maximum load factor to 1.0
```

<br>

---

<br>

## Other Operations

<br>

#### `swap`

- **Description:** Swaps the content of two unordered sets.
- **Complexity:** $O(1)$

```cpp
std::unordered_set<int> us2 = {9, 8, 7};
us.swap(us2); // Swaps content of us and us2
```

<br>

#### `assign`

- **Description:** Assigns new values to the unordered set, replacing the old ones.
- **Complexity:** $O(n)$

```cpp
us = {5, 6, 7, 8}; // Assigns new values to the unordered set
```

<br>

---

<br>

## Hash Policy

<br>

`std::unordered_set` uses a hash policy to manage the number of buckets and control when the container should be rehashed.

<br>

#### `rehash`

- **Description:** Rehashes the unordered set so that it contains at least the specified number of buckets.
- **Complexity:** $O(n)$

```cpp
us.rehash(20); // Rehashes the unordered set to have at least 20 buckets
```

<br>

#### `reserve`

- **Description:** Reserves enough space to hold the specified number of elements without rehashing.
- **Complexity:** $O(n)$

```cpp
us.reserve(50); // Reserves space for 50 elements
```

<br>

---

<br>

## Custom Hash Functions

<br>

`std::unordered_set` allows the use of custom hash functions and comparison functions to control how elements are stored and compared.

<br>

#### Example of a custom hash function:

```cpp
struct CustomHash {
    std::size_t operator()(int x) const {
        return x % 10;
    }
};
std::unordered_set<int, CustomHash> us;
```

<br>

In this example, the custom hash function stores elements based on their remainder when divided by 10.

<br>

---

<br>

## Special Properties of `std::unordered_set`

- Elements are not ordered.
- Average $O(1)$ time complexity for insertion, deletion, and lookup.
- Allows custom hash functions and comparison functions.
- Uses buckets and a hash function to organize elements.
