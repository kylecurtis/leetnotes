`std::set` is an associative container that stores unique elements in a specific order. The elements are sorted based on a comparison function, by default `std::less<Key>`, and internally implemented as a self-balancing binary search tree (usually a Red-Black tree). `std::set` ensures that no two elements are equal, and provides logarithmic time complexity for insertions, deletions, and searches.

<br>

---

<br>

## Header File

To use `std::set`, you need to include the following header:

```cpp
#include <set>
```

<br>

---

<br>

## Time/Space Complexities Summary

| Function               | Time Complexity  | Space Complexity |
|------------------------|------------------|------------------|
| Constructor (default)   | O(1)             | O(1)             |
| Constructor (range)     | O(n log n)       | O(n)             |
| insert()               | O(log n)         | O(log n)         |
| erase()                | O(log n)         | O(log n)         |
| find()                 | O(log n)         | O(1)             |
| count()                | O(log n)         | O(1)             |
| clear()                | O(n)             | O(1)             |
| swap()                 | O(1)             | O(1)             |

<br>

---

<br>

## Constructor

<br>

### std::set()

**Description:** Constructs an empty set.

**Template Syntax:**

```cpp
std::set<data_type> set_name;
```

- `data_type`: The type of the keys stored in the set.
- `set_name`: The name of the set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::set<int> s;
```

<br>

### std::set(InputIt first, InputIt last)

**Description:** Constructs a set from a range defined by iterators `[first, last)`.

**Template Syntax:**

```cpp
std::set<data_type> set_name(iterator_first, iterator_last);
```

- `data_type`: The type of the keys stored in the set.
- `set_name`: The name of the set.
- `iterator_first`, `iterator_last`: Iterators defining the range of elements to insert.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n log n) | O(n) |

```cpp
std::vector<int> vec = {1, 2, 3};
std::set<int> s(vec.begin(), vec.end());
```

<br>

### std::set(std::initializer_list<T> init)

**Description:** Constructs a set initialized with elements from an initializer list.

**Template Syntax:**

```cpp
std::set<data_type> set_name = {value1, value2, value3, ...};
```

- `data_type`: The type of the keys stored in the set.
- `set_name`: The name of the set.
- `value1, value2, value3, ...`: The values to initialize the set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n log n) | O(n) |

```cpp
std::set<int> s = {1, 2, 3};  // Creates a set with elements 1, 2, and 3.
```

<br>

---

<br>

## Capacity Functions

<br>

### size()

**Description:** Returns the number of elements in the set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::set<int> s = {1, 2, 3};
size_t sz = s.size(); // sz = 3
```

<br>

### empty()

**Description:** Checks if the set contains no elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::set<int> s;
bool is_empty = s.empty(); // true
```

<br>

### max_size()

**Description:** Returns the maximum number of elements that the set can hold.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::set<int> s;
size_t max_sz = s.max_size();
```

<br>

---

<br>

## Modifiers

<br>

### insert(const T& value)

**Description:** Inserts a unique element into the set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(log n) |

```cpp
std::set<int> s = {1, 2, 3};
s.insert(4); // Inserts 4 into the set.
```

<br>

### insert(InputIt first, InputIt last)

**Description:** Inserts elements from the range `[first, last)`.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n log n) | O(n) |

```cpp
std::vector<int> vec = {4, 5, 6};
s.insert(vec.begin(), vec.end());  // Inserts elements from the vector into the set.
```

<br>

### emplace(Args&&... args)

**Description:** Constructs an element in place within the set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(log n) |

```cpp
std::set<int> s;
s.emplace(4); // Constructs 4 directly in the set.
```

<br>

### erase(iterator pos)

**Description:** Erases the element at the specified position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::set<int> s = {1, 2, 3};
s.erase(s.begin()); // Erases the first element (1).
```

<br>

### clear()

**Description:** Clears the set by removing all elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::set<int> s = {1, 2, 3};
s.clear(); // Empties the set.
```

<br>

### swap(std::set& other)

**Description:** Swaps the contents of two sets.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::set<int> s1 = {1, 2, 3};
std::set<int> s2 = {4, 5, 6};
s1.swap(s2);  // s1 becomes {4, 5, 6}, and s2 becomes {1, 2, 3}.
```

<br>

---

<br>

## Lookup Functions

<br>

### find(const Key& key)

**Description:** Finds an element with the given `key` and returns an iterator to it, or `end()` if not found.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::set<int> s = {1, 2, 3};
auto it = s.find(2);  // Returns an iterator to 2.
```

<br>

### count(const Key& key)

**Description:** Returns the number of elements matching the key (0 or 1 since elements are unique in a set).

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::set<int> s = {1, 2, 3};
size_t count = s.count(2);  // count = 1
```

<br>

### contains(const Key& key)

**Description:** Checks whether the set contains an element with the specified `key`.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::set<int> s = {1, 2, 3};
bool exists = s.contains(2);  // true
```

<br>

---

<br>

## Iterators

<br>

### begin()

**Description:** Returns an iterator to the first element in the set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::set<int> s = {1, 2, 3};
auto it = s.begin();  // Points to the first element.
```

<br>

### end()

**Description:** Returns an iterator to the element following the last element in the set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::set<int> s = {1, 2, 3};
auto it = s.end();  // Points to the past-the-end element.
```

<br>

---

<br>

## Observers

<br>

### key_comp()

**Description:** Returns the function that compares the keys.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::set<int> s;
auto comp = s.key_comp();
```

<br>

### value_comp()

**Description:** Returns a function that compares values.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::set<int> s;
auto comp = s.value_comp();
```

<br>

---

<br>

## Non-Member Functions

<br>

### operator ==

**Description:** Lexicographically compares two sets for equality.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

### operator <=>

**Description:** Compares sets using the three-way comparison operator.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

### std::swap

**Description:** Specializes `std::swap` for sets.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

<br>

---

<br>

## Member Types

| Member Type        | Description                                    |
|--------------------|------------------------------------------------|
| `key_type`         | Type of the keys stored in the set.             |
| `value_type`       | Same as `key_type`.                             |
| `size_type`        | Unsigned integer type representing the size.    |
| `difference_type`  | Signed integer type for pointer differences.    |
| `key_compare`      | The key comparison function.                    |
| `value_compare`    | The value comparison function.                  |
| `allocator_type`   | The allocator used to allocate memory.          |
| `iterator`         | Constant bidirectional iterator to `value_type`.|
| `const_iterator`   | Bidirectional iterator to `const value_type`.   |
