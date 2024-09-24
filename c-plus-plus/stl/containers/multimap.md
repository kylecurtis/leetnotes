`std::multimap` is an associative container that stores key-value pairs in sorted order, allowing multiple elements with the same key. It maintains the order of insertion for elements with equivalent keys, and the elements are sorted based on a comparison function (by default, `std::less<Key>`). Like `std::map`, it provides logarithmic complexity for insertions, deletions, and searches. Internally, it is implemented as a balanced binary search tree (typically a Red-Black Tree).

<br>

---

<br>

## Header File

To use `std::multimap`, include the following header:

```cpp
#include <map>
```

<br>

---

<br>

## Time/Space Complexities Summary

| Operation                | Time Complexity  | Space Complexity |
|--------------------------|------------------|------------------|
| Constructor (default)     | O(1)             | O(1)             |
| Constructor (range)       | O(n log n)       | O(n)             |
| insert()                 | O(log n)         | O(log n)         |
| erase()                  | O(log n)         | O(log n)         |
| find()                   | O(log n)         | O(1)             |
| count()                  | O(log n)         | O(1)             |
| clear()                  | O(n)             | O(1)             |
| swap()                   | O(1)             | O(1)             |
| lower_bound()/upper_bound() | O(log n)         | O(1)             |
| equal_range()            | O(log n)         | O(1)             |

<br>

---

<br>

## Constructor

<br>

### std::multimap()

**Description:** Constructs an empty multimap.

**Template Syntax:**

```cpp
std::multimap<Key, T> multimap_name;
```

- `Key`: Type of the keys.
- `T`: Type of the values.
- `multimap_name`: Name of the multimap.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multimap<int, std::string> mm;
```

<br>

### std::multimap(InputIt first, InputIt last)

**Description:** Constructs a multimap from a range defined by iterators `[first, last)`.

**Template Syntax:**

```cpp
std::multimap<Key, T> multimap_name(iterator_first, iterator_last);
```

- `Key`: Type of the keys.
- `T`: Type of the values.
- `iterator_first`, `iterator_last`: Iterators defining the range of elements to insert.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n log n) | O(n) |

```cpp
std::vector<std::pair<int, std::string>> vec = {{1, "one"}, {2, "two"}};
std::multimap<int, std::string> mm(vec.begin(), vec.end());
```

<br>

---

<br>

## Capacity Functions

<br>

### size()

**Description:** Returns the number of elements in the multimap.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multimap<int, std::string> mm = {{1, "one"}, {2, "two"}};
size_t sz = mm.size(); // sz = 2
```

<br>

### empty()

**Description:** Checks if the multimap contains no elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multimap<int, std::string> mm;
bool is_empty = mm.empty(); // true
```

<br>

### max_size()

**Description:** Returns the maximum number of elements that the multimap can hold.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multimap<int, std::string> mm;
size_t max_sz = mm.max_size();
```

<br>

---

<br>

## Modifiers

<br>

### insert(const std::pair<Key, T>& value)

**Description:** Inserts an element into the multimap, allowing duplicates.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(log n) |

```cpp
std::multimap<int, std::string> mm = {{1, "one"}, {2, "two"}};
mm.insert({2, "another two"}); // Inserts the pair {2, "another two"}
```

<br>

### insert_or_assign(Key key, T value) *(C++17)*

**Description:** Inserts or assigns an element. If the key exists, it assigns a new value.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::multimap<int, std::string> mm = {{1, "one"}};
mm.insert_or_assign(1, "ONE"); // Assigns "ONE" to the key 1
```

<br>

### erase(iterator pos)

**Description:** Erases the element at the specified position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(log n) |

```cpp
std::multimap<int, std::string> mm = {{1, "one"}, {2, "two"}};
mm.erase(mm.begin()); // Erases the first element
```

<br>

### clear()

**Description:** Clears the multimap by removing all elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::multimap<int, std::string> mm = {{1, "one"}, {2, "two"}};
mm.clear(); // Empties the multimap
```

<br>

---

<br>

## Lookup Functions

<br>

### find(const Key& key)

**Description:** Finds an element with the given key and returns an iterator to it, or `end()` if not found.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::multimap<int, std::string> mm = {{1, "one"}, {2, "two"}};
auto it = mm.find(1);  // Finds the element with key 1
```

<br>

### count(const Key& key)

**Description:** Returns the number of elements matching the key.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::multimap<int, std::string> mm = {{1, "one"}, {2, "two"}, {2, "duplicate"}};
size_t count = mm.count(2);  // count = 2
```

<br>

### equal_range(const Key& key)

**Description:** Returns a pair of iterators denoting the range of elements that are equivalent to the key.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::multimap<int, std::string> mm = {{1, "one"}, {2, "two"}, {2, "another two"}};
auto range = mm.equal_range(2);  // Returns a pair of iterators to the range of elements with key 2
```

<br>

---

<br>

## Iterators

<br>

### begin()

**Description:** Returns an iterator to the first element in the multimap.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multimap<int, std::string> mm = {{1, "one"}, {2, "two"}};
auto it = mm.begin();  // Points to the first element
```

<br>

### end()

**Description:** Returns an iterator to the element following the last element in the multimap.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multimap<int, std::string> mm = {{1, "one"}, {2, "two"}};
auto it = mm.end();  // Points to the past-the-end element
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
std::multimap<int, std::string> mm;
auto comp = mm.key_comp();
```

<br>

### value_comp()

**Description:** Returns a function that compares values in the multimap.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::multimap<int, std::string> mm;
auto comp = mm.value_comp();
```

<br>

---

<br>

## Non-Member Functions

<br>

### operator==

**Description:** Compares two multimaps for equality.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

### std::swap

**Description:** Specializes `std::swap` for multimaps.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |