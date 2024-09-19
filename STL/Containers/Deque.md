`std::deque` is a double-ended queue that allows fast insertions and deletions at both ends (front and back). It provides random access and behaves similarly to `std::vector`, but with more flexibility regarding insertion and deletion at the front.

<br>

---

<br>

## Header File

To use `std::deque`, you need to include the following header:

```cpp
#include <deque>
```

<br>

---

<br>

## Time/Space Complexities Summary

| Operation               | Time Complexity | Space Complexity |
|-------------------------|-----------------|------------------|
| Constructor (default)    | O(1)            | O(1)             |
| Constructor (range)      | O(n)            | O(n)             |
| Access (at, [])          | O(1)            | O(1)             |
| Insert (front)           | O(1)            | O(n) (if reallocation) |
| Insert (back)            | O(1)            | O(n) (if reallocation) |
| Insert (middle)          | O(n)            | O(n)             |
| Erase (front)            | O(1)            | O(n)             |
| Erase (back)             | O(1)            | O(n)             |
| Erase (middle)           | O(n)            | O(n)             |
| Push Front               | O(1)            | O(n) (if reallocation) |
| Push Back                | O(1)            | O(n) (if reallocation) |
| Pop Front                | O(1)            | O(1)             |
| Pop Back                 | O(1)            | O(1)             |
| Size                     | O(1)            | O(1)             |
| Clear                    | O(n)            | O(1)             |
| Resize                   | O(n)            | O(n)             |

<br>

---

<br>

## Constructor

<br>

### std::deque()

**Description:** Constructs an empty deque.

**Template Syntax:**

```cpp
std::deque<data_type> deque_name;
```

- `data_type`: The type of the elements stored in the deque.
- `deque_name`: The name of the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::deque<int> deq;
```

<br>

### std::deque(InputIt first, InputIt last)

**Description:** Constructs a deque from a range defined by iterators `[first, last)`.

**Template Syntax:**

```cpp
std::deque<data_type> deque_name(iterator_first, iterator_last);
```

- `data_type`: The type of the elements stored in the deque.
- `deque_name`: The name of the deque.
- `iterator_first`, `iterator_last`: Iterators defining the range of elements to insert.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::vector<int> vec = {1, 2, 3};
std::deque<int> deq(vec.begin(), vec.end());
```

<br>

### std::deque(std::initializer_list<T> init)

**Description:** Constructs a deque initialized with elements from an initializer list.

**Template Syntax:**

```cpp
std::deque<data_type> deque_name = {value1, value2, value3, ...};
```

- `data_type`: The type of the elements stored in the deque.
- `deque_name`: The name of the deque.
- `value1, value2, value3, ...`: The values to initialize the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::deque<int> deq = {1, 2, 3};  // Creates a deque with elements 1, 2, and 3.
```

<br>

---

<br>

## Modifiers

<br>

### push_back(const T& value)

**Description:** Adds an element to the back of the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(n) (if reallocation) |

```cpp
deq.push_back(5);  // Adds 5 to the back of the deque.
```

<br>

### push_front(const T& value)

**Description:** Adds an element to the front of the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(n) (if reallocation) |

```cpp
deq.push_front(10);  // Adds 10 to the front of the deque.
```

<br>

### emplace_back(Args&&... args)

**Description:** Constructs and adds an element to the back of the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(n) (if reallocation) |

```cpp
deq.emplace_back(15);  // Constructs and adds 15 to the back of the deque.
```

<br>

### emplace_front(Args&&... args)

**Description:** Constructs and adds an element to the front of the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(n) (if reallocation) |

```cpp
deq.emplace_front(20);  // Constructs and adds 20 to the front of the deque.
```

<br>

### insert(const_iterator pos, const T& value)

**Description:** Inserts an element at the specified position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
deq.insert(deq.begin() + 1, 100);  // Inserts 100 at position 1.
```

<br>

### erase(const_iterator pos)

**Description:** Removes an element from the specified position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
deq.erase(deq.begin() + 2);  // Removes the element at position 2.
```

<br>

### pop_back()

**Description:** Removes the last element from the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
deq.pop_back();  // Removes the last element.
```

<br>

### pop_front()

**Description:** Removes the first element from the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
deq.pop_front();  // Removes the first element.
```

<br>

### clear()

**Description:** Removes all elements from the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
deq.clear();  // Removes all elements from the deque.
```

<br>

---

<br>

## Element Access

<br>

### operator[] (subscript) and at()

**Description:** Accesses an element at the given position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
int x = deq[0];  // Accesses the first element (no bounds checking).
int y = deq.at(2);  // Accesses the third element (with bounds checking).
```

<br>

### front() and back()

**Description:** Accesses the first or last element of the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
int first = deq.front();  // Accesses the first element.
int last = deq.back();  // Accesses the last element.
```

<br>

---

<br>

## Capacity

<br>

### size()

**Description:** Returns the number of elements in the deque.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::size_t sz = deq.size();  // Returns the number of elements.
```

<br>

### empty()

**Description:** Checks if the deque is empty.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
bool isEmpty = deq.empty();  // Returns true if the deque is empty.
```

<br>

### resize(size_type count)

**Description:** Resizes the deque to contain `count` elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
deq.resize(20);  // Resizes the deque to hold 20 elements.
deq.resize(5);  // Shrinks the deque to 5 elements.
```

<br>

---

<br>

## Iterators

<br>

### begin(), end(), rbegin(), rend()

**Description:** Provides iterators for range-based loops and algorithms.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
for (auto it = deq.begin(); it != deq.end(); ++it) {
    std::cout << *it << " ";
}

for (auto rit = deq.rbegin(); rit != deq.rend(); ++rit) {
    std::cout << *rit << " ";
}
```

<br>

---

<br>

## Other Operations

<br>

### swap(std::deque& other)

**Description:** Swaps the contents of two deques.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::deque<int> deq2 = {9, 8, 7};
deq.swap(deq2);  // Swaps contents of deq and deq2.
```

<br>

### assign(size_type count, const T& value)

**Description:** Assigns new values to the deque, replacing its contents.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
deq.assign(5, 100);  // Assigns 5 elements with the value 100.
deq.assign({1, 2, 3, 4});  // Assigns an initializer list.
```

<br>

---

<br>

## Member Types

| Member Type        | Description                                    |
|--------------------|------------------------------------------------|
| `value_type`       | Type of elements in the deque.                  |
| `allocator_type`   | Allocator used to allocate memory.              |
| `size_type`        | Unsigned integer type representing the size.    |
| `difference_type`  | Signed integer type for pointer differences.    |
| `reference`        | Reference to `value_type`.                      |
| `const_reference`  | Constant reference to `value_type`.             |
| `pointer`          | Pointer to `value_type`.                        |
| `const_pointer`    | Constant pointer to `value_type`.               |
| `iterator`         | Random-access iterator to `value_type`.         |
| `const_iterator`   | Constant random-access iterator to `const value_type`. |
| `reverse_iterator` | Reverse iterator to `value_type`.               |
| `const_reverse_iterator` | Constant reverse iterator to `const value_type`. |
