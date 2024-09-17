`std::list` is a doubly linked list that supports constant time insertion and removal of elements from anywhere in the container. It allows for efficient bidirectional traversal, but does not provide fast random access (unlike `std::vector`). It is more memory-efficient than `std::forward_list`, which only supports singly linked lists.

<br>

---

<br>

## Header File

To use `std::list`, you need to include the following header:

```cpp
#include <list>
```

<br>

---

<br>

## Time/Space Complexities Summary

| Function               | Time Complexity  | Space Complexity |
|------------------------|------------------|------------------|
| Constructor (default)   | O(1)             | O(1)             |
| Constructor (range)     | O(n)             | O(n)             |
| insert()               | O(1)             | O(1)             |
| erase()                | O(1)             | O(1)             |
| find()                 | O(n)             | O(1)             |
| clear()                | O(n)             | O(1)             |
| push_back()            | O(1)             | O(1)             |
| push_front()           | O(1)             | O(1)             |
| pop_back()             | O(1)             | O(1)             |
| pop_front()            | O(1)             | O(1)             |
| merge()                | O(n)             | O(1)             |
| sort()                 | O(n log n)       | O(1)             |
| splice()               | O(1)             | O(1)             |

<br>

---

<br>

## Constructor

<br>

### std::list()

**Description:** Constructs an empty list.

**Template Syntax:**

```cpp
std::list<data_type> list_name;
```

- `data_type`: The type of the elements stored in the list.
- `list_name`: The name of the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst;
```

<br>

### std::list(InputIt first, InputIt last)

**Description:** Constructs a list from a range defined by iterators `[first, last)`.

**Template Syntax:**

```cpp
std::list<data_type> list_name(iterator_first, iterator_last);
```

- `data_type`: The type of the elements stored in the list.
- `list_name`: The name of the list.
- `iterator_first`, `iterator_last`: Iterators defining the range of elements to insert.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::vector<int> vec = {1, 2, 3};
std::list<int> lst(vec.begin(), vec.end());
```

<br>

### std::list(std::initializer_list<T> init)

**Description:** Constructs a list initialized with elements from an initializer list.

**Template Syntax:**

```cpp
std::list<data_type> list_name = {value1, value2, value3, ...};
```

- `data_type`: The type of the elements stored in the list.
- `list_name`: The name of the list.
- `value1, value2, value3, ...`: The values to initialize the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::list<int> lst = {1, 2, 3};  // Creates a list with elements 1, 2, and 3.
```

<br>

---

<br>

## Capacity Functions

<br>

### size()

**Description:** Returns the number of elements in the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
size_t sz = lst.size(); // sz = 3
```

<br>

### empty()

**Description:** Checks if the list contains no elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst;
bool is_empty = lst.empty(); // true
```

<br>

### max_size()

**Description:** Returns the maximum number of elements that the list can hold.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst;
size_t max_sz = lst.max_size();
```

<br>

---

<br>

## Modifiers

<br>

### insert(iterator pos, const T& value)

**Description:** Inserts an element at the specified position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
lst.insert(++lst.begin(), 4); // Inserts 4 after the first element.
```

<br>

### erase(iterator pos)

**Description:** Erases the element at the specified position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
lst.erase(++lst.begin()); // Erases the second element (2).
```

<br>

### clear()

**Description:** Clears the list by removing all elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
lst.clear(); // Empties the list.
```

<br>

### push_back(const T& value)

**Description:** Adds an element to the end of the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
lst.push_back(4); // Adds 4 to the end of the list.
```

<br>

### push_front(const T& value)

**Description:** Adds an element to the beginning of the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
lst.push_front(0); // Adds 0 to the front of the list.
```

<br>

### pop_back()

**Description:** Removes the last element from the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
lst.pop_back(); // Removes the last element (3).
```

<br>

### pop_front()

**Description:** Removes the first element from the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
lst.pop_front(); // Removes the first element (1).
```

<br>

---

<br>

## Iterators

<br>

### begin()

**Description:** Returns an iterator to the first element in the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
auto it = lst.begin();  // Points to the first element.
```

<br>

### end()

**Description:** Returns an iterator to the element following the last element in the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
auto it = lst.end();  // Points to the past-the-end element.
```

<br>

### rbegin()

**Description:** Returns a reverse iterator to the first element of the reversed list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
auto rit = lst.rbegin();  // Points to the last element (in reverse order).
```

<br>

### rend()

**Description:** Returns a reverse iterator to the element following the last element of the reversed list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
auto rit = lst.rend();  // Points to the past-the-end element in reverse order.
```

<br>

---

<br>

## Operations

<br>

### sort()

**Description:** Sorts the elements in the list in ascending order.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n log n) | O(1) |



```cpp
std::list<int> lst = {3, 1, 2};
lst.sort(); // Sorts the list to {1, 2, 3}.
```

<br>

### reverse()

**Description:** Reverses the order of the elements in the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::list<int> lst = {1, 2, 3};
lst.reverse(); // Reverses the list to {3, 2, 1}.
```

<br>

### merge(std::list& other)

**Description:** Merges two sorted lists into one sorted list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::list<int> lst1 = {1, 3, 5};
std::list<int> lst2 = {2, 4, 6};
lst1.merge(lst2); // Merges lst2 into lst1.
```

<br>

### splice(const_iterator pos, std::list& other)

**Description:** Transfers elements from another list into this list at the specified position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst1 = {1, 2, 3};
std::list<int> lst2 = {4, 5, 6};
lst1.splice(lst1.end(), lst2);  // Moves all elements of lst2 into lst1.
```

<br>

---

<br>

## Observers

<br>

### get_allocator()

**Description:** Returns the allocator used by the list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::list<int> lst;
auto alloc = lst.get_allocator();
```

<br>

---

<br>

## Non-Member Functions

<br>

### operator ==

**Description:** Lexicographically compares two lists for equality.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

### std::swap

**Description:** Specializes `std::swap` for lists.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

<br>

---

<br>

## Member Types

| Member Type        | Description                                    |
|--------------------|------------------------------------------------|
| `value_type`       | Type of elements in the list.                   |
| `allocator_type`   | Allocator used to allocate memory.              |
| `size_type`        | Unsigned integer type representing the size.    |
| `difference_type`  | Signed integer type for pointer differences.    |
| `reference`        | Reference to `value_type`.                      |
| `const_reference`  | Constant reference to `value_type`.             |
| `pointer`          | Pointer to `value_type`.                        |
| `const_pointer`    | Constant pointer to `value_type`.               |
| `iterator`         | Bidirectional iterator to `value_type`.         |
| `const_iterator`   | Constant bidirectional iterator to `value_type`.|
| `reverse_iterator` | Reverse iterator to `value_type`.               |
| `const_reverse_iterator` | Constant reverse iterator to `value_type`.|
