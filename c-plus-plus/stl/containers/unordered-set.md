`std::unordered_set` is an associative container that stores unique elements in an unordered fashion, based on the element's hash value. It provides average constant-time complexity for search, insertion, and deletion operations. Internally, the elements are organized into buckets, and their location is determined by their hash.

<br>

---

<br>

## Header File

To use `std::unordered_set`, you need to include the following header:

```cpp
#include <unordered_set>
```

<br>

---

<br>

## Time/Space Complexities Summary

| Function                  | Time Complexity  | Space Complexity |
|---------------------------|------------------|------------------|
| Constructor (default)      | O(1)             | O(1)             |
| Constructor (range)        | O(n)             | O(n)             |
| insert()                  | O(1) average     | O(1) average     |
| emplace()                 | O(1) average     | O(1) average     |
| emplace_hint()            | O(1) average     | O(1) average     |
| erase(iterator)           | O(1) average     | O(1)             |
| erase(key)                | O(1) average     | O(1)             |
| find()                    | O(1) average     | O(1)             |
| count()                   | O(1) average     | O(1)             |
| clear()                   | O(n)             | O(1)             |
| swap()                    | O(n)             | O(1)             |
| rehash()                  | O(n)             | O(n)             |
| reserve()                 | O(n)             | O(n)             |
| load_factor()             | O(1)             | O(1)             |
| max_load_factor()         | O(1)             | O(1)             |
| bucket_count()            | O(1)             | O(1)             |
| bucket_size()             | O(1)             | O(1)             |
| bucket()                  | O(1)             | O(1)             |
| hash_function()           | O(1)             | O(1)             |
| key_eq()                  | O(1)             | O(1)             |

<br>

---

<br>

## Constructor

### std::unordered_set()

**Description:** Constructs an empty unordered set.

**Template Syntax:**

```cpp
std::unordered_set<data_type> set_name;
```

- `data_type`: The type of the keys stored in the unordered set.
- `set_name`: The name of the unordered set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s;
```

<br>

### std::unordered_set(InputIt first, InputIt last)

**Description:** Constructs an unordered set from a range defined by iterators `[first, last)`.

**Template Syntax:**

```cpp
std::unordered_set<data_type> set_name(iterator_first, iterator_last);
```

- `data_type`: The type of the keys stored in the unordered set.
- `set_name`: The name of the unordered set.
- `iterator_first`, `iterator_last`: Iterators defining the range of elements to insert.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::vector<int> vec = {1, 2, 3};
std::unordered_set<int> s(vec.begin(), vec.end());
```

<br>

### std::unordered_set(std::initializer_list<T> init)

**Description:** Constructs an unordered set initialized with elements from an initializer list.

**Template Syntax:**

```cpp
std::unordered_set<data_type> set_name = {value1, value2, value3, ...};
```

- `data_type`: The type of the keys stored in the unordered set.
- `set_name`: The name of the unordered set.
- `value1, value2, value3, ...`: The values to initialize the set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::unordered_set<int> s = {1, 2, 3};  // Creates a set with elements 1, 2, and 3.
```

<br>

---

<br>

## Capacity Functions

### size()

**Description:** Returns the number of elements in the unordered set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
size_t sz = s.size(); // sz = 3
```

<br>

### empty()

**Description:** Checks if the unordered set contains no elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s;
bool is_empty = s.empty(); // true
```

<br>

### max_size()

**Description:** Returns the maximum number of elements that the unordered set can hold.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s;
size_t max_sz = s.max_size();
```

<br>

---

<br>

## Modifiers

### insert(const T& value)

**Description:** Inserts a unique element into the unordered set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) average | O(1) average |

```cpp
std::unordered_set<int> s = {1, 2, 3};
s.insert(4); // Inserts 4 into the set.
```

<br>

### emplace(Args&&... args)

**Description:** Constructs an element in place within the unordered set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) average | O(1) average |

```cpp
std::unordered_set<int> s;
s.emplace(4); // Constructs 4 directly in the unordered set.
```

<br>

### emplace_hint(const_iterator hint, Args&&... args)

**Description:** Constructs an element in place within the unordered set, using a hint for insertion position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) average | O(1) average |

```cpp
std::unordered_set<int> s = {1, 2, 3};
auto it = s.emplace_hint(s.begin(), 4);  // Constructs 4 in place with a hint.
```

<br>

### erase(iterator pos)

**Description:** Erases the element at the specified position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) average | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
s.erase(s.begin()); // Erases the first element.
```

<br>

### erase(const Key& key)

**Description:** Removes the element corresponding to the key value.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) average | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
s.erase(2);  // Removes the element with key 2.
```

<br>

### clear()

**Description:** Clears the unordered set by removing all elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
s.clear(); // Empties the set.
```

<br>

### swap(std::unordered_set& other)

**Description:** Swaps the contents of two unordered sets.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::unordered_set<int> s1 = {1, 2, 3};
std::unordered_set<int> s2 = {4, 5, 6};
s1.swap(s2);  // s1 becomes {4, 5, 6}, and s2 becomes {1, 2, 3}.
```

<br>

---

<br>

## Lookup Functions

### find(const Key& key)

**Description:** Finds an element with the given `key` and returns an iterator to it, or `end()` if not found.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) average | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
auto it = s.find(2);  // Returns an iterator to 2.
```

<br>

### count(const Key& key)

**Description:** Returns the number of elements matching the key (0 or 1 since elements are unique in a set).

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) average | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
size_t count = s.count(2);  // count = 1
```

<br>

### contains(const Key& key)

**Description:** Checks whether the unordered set contains an element with the specified `key`.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) average | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
bool exists = s.contains(2);  // true
```

<br>

---

<br>

## Hash Policy

### load_factor()

**Description:** Returns the average number of elements per bucket in the unordered set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
float lf = s.load_factor(); // Returns the current load factor.
```

<br>

### max_load_factor()

**Description:** Sets the maximum load factor that controls when the unordered set will automatically rehash.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s;
s.max_load_factor(0.75f); // Sets the maximum load factor to 0.75.
```

<br>

### rehash(size_type count)

**Description:** Rehashes the unordered set to ensure it has at least `count` buckets.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
s.rehash(10); // Rehashes the set with at least 10 buckets.
```

<br>

### reserve(size_type count)

**Description:** Reserves space for `count` elements, potentially reducing rehashes.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::unordered_set<int> s;
s.reserve(100);  // Reserves space for 100 elements.
```

<br>

---

<br>

## Bucket Interface

### bucket_count()

**Description:** Returns the number of buckets in the unordered set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
size_t bucket_cnt = s.bucket_count();  // Returns the number of buckets.
```

<br>

### bucket_size(size_type n)

**Description:** Returns the number of elements in bucket `n`.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
size_t bucket_sz = s.bucket_size(0);  // Returns the number of elements in bucket 0.
```

<br>

### bucket(const Key& key)

**Description:** Returns the bucket index where the element with the given key is located.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s = {1, 2, 3};
size_t bucket_idx = s.bucket(2);  // Returns the bucket index for key 2.
```

<br>

---

<br>

## Observers

### hash_function()

**Description:** Returns the hash function used by the unordered set.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s;
auto hash_fn = s.hash_function();  // Retrieves the hash function.
```

<br>

### key_eq()

**Description:** Returns the key equality comparison function.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::unordered_set<int> s;
auto key_eq_fn = s.key_eq();  // Retrieves the key equality comparison function.
```

<br>

---

<br>

## Non-Member Functions

### operator ==

**Description:** Lexicographically compares two unordered sets for equality.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

### std::swap

**Description:** Specializes `std::swap` for unordered sets.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

<br>

---

<br>

## Member Types

| Member Type        | Description                                    |
|--------------------|------------------------------------------------|
| `key_type`         | Type of the keys stored in the unordered set.   |
| `value_type`       | Same as `key_type`.                             |
| `size_type`        | Unsigned integer type representing the size.    |
| `difference_type`  | Signed integer type for pointer differences.    |
| `hasher`           | The hash function used to hash the keys.        |
| `key_equal`        | The key comparison function.                    |
| `allocator_type`   | The allocator used to allocate memory.          |
| `iterator`         | Forward iterator to `value_type`.               |
| `const_iterator`   | Constant forward iterator to `const value_type`.|