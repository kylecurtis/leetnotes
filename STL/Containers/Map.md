`std::map` is a sorted associative container that stores key-value pairs, where keys are unique and elements are stored in a specific order determined by a comparison function (`std::less<Key>` by default). It provides logarithmic complexity for search, insertion, and removal operations. Internally, it is implemented as a balanced binary search tree (commonly a Red-Black Tree).

<br>

---

<br>

## Header File

To use `std::map`, include the following header:

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
| at()                     | O(log n)         | O(1)             |
| operator[]               | O(log n)         | O(1)             |
| clear()                  | O(n)             | O(1)             |
| swap()                   | O(1)             | O(1)             |
| lower_bound()/upper_bound() | O(log n)         | O(1)             |
| equal_range()            | O(log n)         | O(1)             |

<br>

---

<br>

## Constructor

<br>

### `std::map()`

**Description:** Constructs an empty map.

**Template Syntax:**

```cpp
std::map<Key, T> map_name;
```

- `Key`: Type of the keys.
- `T`: Type of the values.
- `map_name`: Name of the map.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::map<int, std::string> m;
```

<br>

### `std::map(InputIt first, InputIt last)`

**Description:** Constructs a map from a range defined by iterators `[first, last)`.

**Template Syntax:**

```cpp
std::map<Key, T> map_name(iterator_first, iterator_last);
```

- `Key`: Type of the keys.
- `T`: Type of the values.
- `iterator_first`, `iterator_last`: Iterators defining the range of elements to insert.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n log n) | O(n) |

```cpp
std::vector<std::pair<int, std::string>> vec = {{1, "one"}, {2, "two"}};
std::map<int, std::string> m(vec.begin(), vec.end());
```

<br>

---

<br>

## Capacity Functions

<br>

### `size()`

**Description:** Returns the number of elements in the map.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::map<int, std::string> m = {{1, "one"}, {2, "two"}};
size_t sz = m.size(); // sz = 2
```

<br>

### `empty()`

**Description:** Checks if the map contains no elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::map<int, std::string> m;
bool is_empty = m.empty(); // true
```

<br>

### `max_size()`

**Description:** Returns the maximum number of elements that the map can hold.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::map<int, std::string> m;
size_t max_sz = m.max_size();
```

<br>

---

<br>

## Modifiers

<br>

### `insert(const std::pair<Key, T>& value)`

**Description:** Inserts an element into the map.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(log n) |

```cpp
std::map<int, std::string> m = {{1, "one"}, {2, "two"}};
m.insert({3, "three"}); // Inserts the pair {3, "three"}
```

<br>

### `insert_or_assign(Key key, T value)`

**Description:** Inserts or assigns an element. If the key exists, it assigns a new value.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::map<int, std::string> m = {{1, "one"}};
m.insert_or_assign(1, "ONE"); // Assigns "ONE" to the key 1
```

<br>

### `erase(iterator pos)`

**Description:** Erases the element at the specified position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(log n) |

```cpp
std::map<int, std::string> m = {{1, "one"}, {2, "two"}};
m.erase(m.begin()); // Erases the first element
```

<br>

### `clear()`

**Description:** Clears the map by removing all elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::map<int, std::string> m = {{1, "one"}, {2, "two"}};
m.clear(); // Empties the map
```

<br>

---

<br>

## Element Access

<br>

### `at(const Key& key)`

**Description:** Returns a reference to the value associated with the given key, with bounds checking.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::map<int, std::string> m = {{1, "one"}};
std::string val = m.at(1); // Access the value associated with key 1
```

<br>

### `operator[]`

**Description:** Accesses or inserts an element with the specified key.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::map<int, std::string> m = {{1, "one"}};
m[2] = "two"; // Inserts a new element with key 2 and value "two"
```

<br>

---

<br>

## Lookup Functions

<br>

### `find(const Key& key)`

**Description:** Finds an element with the given key and returns an iterator to it, or `end()` if not found.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::map<int, std::string> m = {{1, "one"}, {2, "two"}};
auto it = m.find(1);  // Finds the element with key 1
```

<br>

### `count(const Key& key)`

**Description:** Returns the number of elements matching the key (0 or 1 since keys are unique).

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(log n) | O(1) |

```cpp
std::map<int, std::string> m = {{1, "one"}, {2, "two"}};
size_t count = m.count(2);  // count = 1
```

<br>

---

<br>

## Iterators

<br>

### `begin()`

**Description:** Returns an iterator to the first element in the map.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::map<int, std::string> m = {{1, "one"}, {2, "two"}};
auto it = m.begin();  // Points to the first element
```

<br>

### `end()`

**Description:** Returns an iterator to the element following the last element in the map.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::map<int, std::string> m = {{1, "one"}, {2, "two"}};
auto it = m.end();  // Points to the past-the-end element
```

<br>

---

<br>

## Observers

<br>

### `key_comp()`

**Description:** Returns the function that compares the keys.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::map<int, std::string> m;
auto comp = m.key_comp();
```

<br>

### `value_comp()`

**Description:** Returns a function that compares values in the map.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::map<int, std::string> m;
auto comp = m.value_comp();
```

<br>

---

<br>

## Non-Member Functions

<br>

### `operator==`

**Description:** Compares two maps for equality.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

### `std::swap`

**Description:** Specializes `std::swap` for maps.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |