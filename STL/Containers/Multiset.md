`std::multiset` is an associative container that contains multiple elements of the same key. Unlike `std::set`, a `std::multiset` allows duplicate elements. The elements are stored in a specific order determined by a comparison function, which by default is `std::less<Key>`. Search, insertion, and removal operations have logarithmic complexity.

<br>

---

<br>

## Header File

To use `std::multiset`, you need to include the following header:

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
| equal_range()          | O(log n)         | O(1)             |

<br>

---

<br>

## Constructor

<br>

### std::multiset()

**Description:** Constructs an empty multiset.

**Template Syntax:**

```cpp
std::multiset<data_type> multiset_name;
```

- `data_type`: The type of the keys stored in the multiset.
- `multiset_name`: The name of the multiset.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multiset<int> ms;
```

<br>

### std::multiset(InputIt first, InputIt last)

**Description:** Constructs a multiset from a range defined by iterators `[first, last)`.

**Template Syntax:**

```cpp
std::multiset<data_type> multiset_name(iterator_first, iterator_last);
```

- `data_type`: The type of the keys stored in the multiset.
- `multiset_name`: The name of the multiset.
- `iterator_first`, `iterator_last`: Iterators defining the range of elements to insert.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n log n) | O(n) |

```cpp
std::vector<int> vec = {1, 2, 3};
std::multiset<int> ms(vec.begin(), vec.end());
```

<br>

### std::multiset(std::initializer_list<T> init)

**Description:** Constructs a multiset initialized with elements from an initializer list.

**Template Syntax:**

```cpp
std::multiset<data_type> multiset_name = {value1, value2, value3, ...};
```

- `data_type`: The type of the keys stored in the multiset.
- `multiset_name`: The name of the multiset.
- `value1, value2, value3, ...`: The values to initialize the multiset.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n log n) | O(n) |

```cpp
std::multiset<int> ms = {1, 2, 3};  // Creates a multiset with elements 1, 2, and 3.
```

<br>

---

<br>

## Capacity Functions

<br>

### size()

**Description:** Returns the number of elements in the multiset.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multiset<int> ms = {1, 2, 3};
size_t sz = ms.size(); // sz = 3
```

<br>

### empty()

**Description:** Checks if the multiset contains no elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multiset<int> ms;
bool is_empty = ms.empty(); // true
```

<br>

### max_size()

**Description:** Returns the maximum number of elements that the multiset can hold.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multiset<int> ms;
size_t max_sz = ms.max_size();
```

<br>

---

<br>

## Modifiers

<br>

### insert(const T& value)

**Description:** Inserts an element into the multiset. Since `std::multiset` allows duplicates, this does not prevent the insertion of elements that are already present.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(log n) |

```cpp
std::multiset<int> ms = {1, 2, 3};
ms.insert(4);  // Inserts 4 into the multiset.
```

<br>

### insert(InputIt first, InputIt last)

**Description:** Inserts elements from the range `[first, last)`.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n log n) | O(n) |

```cpp
std::vector<int> vec = {4, 5, 6};
ms.insert(vec.begin(), vec.end());  // Inserts elements from the vector into the multiset.
```

<br>

### emplace(Args&&... args)

**Description:** Constructs an element in place within the multiset.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(log n) |

```cpp
std::multiset<int> ms;
ms.emplace(4); // Constructs 4 directly in the multiset.
```

<br>

### erase(iterator pos)

**Description:** Erases the element at the specified position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::multiset<int> ms = {1, 2, 3};
ms.erase(ms.begin()); // Erases the first element (1).
```

<br>

### clear()

**Description:** Clears the multiset by removing all elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::multiset<int> ms = {1, 2, 3};
ms.clear(); // Empties the multiset.
```

<br>

### swap(std::multiset& other)

**Description:** Swaps the contents of two multisets.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multiset<int> ms1 = {1, 2, 3};
std::multiset<int> ms2 = {4, 5, 6};
ms1.swap(ms2);  // ms1 becomes {4, 5, 6}, and ms2 becomes {1, 2, 3}.
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
std::multiset<int> ms = {1, 2, 3};
auto it = ms.find(2);  // Returns an iterator to 2.
```

<br>

### count(const Key& key)

**Description:** Returns the number of elements matching the key.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::multiset<int> ms = {1, 2, 3, 3};
size_t count = ms.count(3);  // count = 2
```

<br>

### equal_range(const Key& key)

**Description:** Returns a pair of iterators denoting the range of elements that are equivalent to the key.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::multiset<int> ms = {1, 2, 3, 3};
auto range = ms.equal_range(3);  // Returns a pair of iterators to the range of elements equal to 3.
```

<br>

---

<br>

## Iterators

<br>

### begin()

**Description:** Returns an iterator to the first element in the multiset.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multiset<int> ms = {1, 2, 3};
auto it = ms.begin();  // Points to the first element.
```

<br>

### end()

**Description:** Returns an iterator to the element following the last element in the multiset.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multiset<int> ms = {1, 2, 3};
auto it = ms.end();  // Points to the past-the-end element.
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
std::multiset<int> ms;
auto comp = ms.key_comp();
```

<br>

### value_comp()

**Description:** Returns a function that compares values in the multiset.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multiset<int> ms;
auto comp = ms.value_comp();
```

<br>

---

<br>

## Non-Member Functions

<br>

### operator ==

**Description:** Lexicographically compares two multisets for equality.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

### std::swap

**Description:** Specializes `std::swap` for multisets.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

<br>

---

<br>

## Member Types

| Member Type        | Description                                    |
|--------------------|------------------------------------------------|
| `key_type`         | Type of the keys stored in the multiset.        |
| `value_type`       | Same as `key_type`.                             |
| `size_type`        | Unsigned integer type representing the size.    |
| `difference_type`  | Signed integer type for pointer differences.    |
| `key_compare`      | The key comparison function.                    |
| `value_compare`    | The value comparison function.                  |
| `allocator_type`   | The allocator used to allocate memory.          |
| `iterator`         | Constant bidirectional iterator to `value_type`.|
| `const_iterator`   | Constant bidirectional iterator to `const value_type`.|
| `reverse_iterator` | Reverse iterator to `value_type`.               |
| `const_reverse_iterator` | Reverse iterator to `const value_type`.   |
