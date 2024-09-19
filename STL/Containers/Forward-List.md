`std::forward_list` is a singly linked list. It is similar to `std::list`, but only supports forward traversal (no reverse iterators). The `std::forward_list` uses less memory compared to `std::list` due to its simple structure but lacks the ability to traverse in reverse or access elements at both ends efficiently.

<br>

---

<br>

## Header File

To use `std::forward_list`, you need to include the following header:

```cpp
#include <forward_list>
```

<br>

---

<br>

## Time/Space Complexities Summary

| Operation               | Time Complexity     | Space Complexity |
|-------------------------|---------------------|------------------|
| Constructor (default)    | O(1)                | O(1)             |
| Constructor (range)      | O(n)                | O(n)             |
| Access (front)           | O(1)                | O(1)             |
| Access (middle)          | O(n)                | O(1)             |
| Insert (front)           | O(1)                | O(1)             |
| Insert (after)           | O(1) + O(n) (traversal) | O(1)         |
| Erase (front)            | O(1)                | O(1)             |
| Erase (after)            | O(1) + O(n) (traversal) | O(1)         |
| Push Front               | O(1)                | O(1)             |
| Pop Front                | O(1)                | O(1)             |
| Size (manual)            | O(n)                | O(1)             |
| Clear                    | O(n)                | O(1)             |
| Sort                     | O(n log n)          | O(1)             |
| Merge                    | O(n)                | O(1)             |
| Remove                   | O(n)                | O(1)             |
| Reverse                  | O(n)                | O(1)             |

<br>

---

<br>

## Constructor

<br>

### std::forward_list()

**Description:** Constructs an empty forward list.

**Template Syntax:**

```cpp
std::forward_list<data_type> list_name;
```

- `data_type`: The type of the elements stored in the forward list.
- `list_name`: The name of the forward list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::forward_list<int> fwd_lst;
```

<br>

### std::forward_list(InputIt first, InputIt last)

**Description:** Constructs a forward list from a range defined by iterators `[first, last)`.

**Template Syntax:**

```cpp
std::forward_list<data_type> list_name(iterator_first, iterator_last);
```

- `data_type`: The type of the elements stored in the forward list.
- `list_name`: The name of the forward list.
- `iterator_first`, `iterator_last`: Iterators defining the range of elements to insert.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::vector<int> vec = {1, 2, 3};
std::forward_list<int> fwd_lst(vec.begin(), vec.end());
```

<br>

### std::forward_list(std::initializer_list<T> init)

**Description:** Constructs a forward list initialized with elements from an initializer list.

**Template Syntax:**

```cpp
std::forward_list<data_type> list_name = {value1, value2, value3, ...};
```

- `data_type`: The type of the elements stored in the forward list.
- `list_name`: The name of the forward list.
- `value1, value2, value3, ...`: The values to initialize the forward list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::forward_list<int> fwd_lst = {1, 2, 3};  // Creates a list with elements 1, 2, and 3.
```

<br>

---

<br>

## Modifiers

<br>

### push_front(const T& value)

**Description:** Adds an element to the front of the forward list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::forward_list<int> fwd_lst = {1, 2, 3};
fwd_lst.push_front(4);  // Adds 4 to the front of the forward list.
```

<br>

### emplace_front(Args&&... args)

**Description:** Constructs and inserts an element at the front of the forward list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
fwd_lst.emplace_front(20); // Constructs and adds 20 to the front of the forward list.
```

<br>

### insert_after(const_iterator pos, const T& value)

**Description:** Inserts an element after the given position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) (insertion) + O(n) (traversal) | O(1) |

```cpp
auto it = fwd_lst.begin();
fwd_lst.insert_after(it, 100);  // Inserts 100 after the first element.
```

<br>

### emplace_after(const_iterator pos, Args&&... args)

**Description:** Constructs and inserts an element after the given position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) (insertion) + O(n) (traversal) | O(1) |

```cpp
fwd_lst.emplace_after(fwd_lst.begin(), 30);  // Constructs 30 in place after the first element.
```

<br>

### erase_after(const_iterator pos)

**Description:** Erases an element after the given position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) (erasure) + O(n) (traversal) | O(1) |

```cpp
fwd_lst.erase_after(fwd_lst.begin());  // Removes the element after the first element.
```

<br>

### pop_front()

**Description:** Removes the first element from the forward list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
fwd_lst.pop_front();  // Removes the first element.
```

<br>

### clear()

**Description:** Removes all elements from the forward list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
fwd_lst.clear();  // Removes all elements from the forward list.
```

<br>

---

<br>

## Lookup

<br>

### front()

**Description:** Accesses the first element of the forward list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
int first = fwd_lst.front();  // Accesses the first element.
```

<br>

---

<br>

## Iterators

<br>

### begin(), end()

**Description:** Provides iterators for range-based loops and algorithms.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
for (auto it = fwd_lst.begin(); it != fwd_lst.end(); ++it) {
    std::cout << *it << " ";
}
```

<br>

---

<br>

## Capacity

<br>

### empty()

**Description:** Checks whether the forward list is empty.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
bool isEmpty = fwd_lst.empty();  // Returns true if the forward list is empty.
```

<br>

### Size Calculation Example

Note that `std::forward_list` does **not** provide a `size()` function because it is a singly linked list. You must manually calculate the size.

```cpp
std::size_t size = std::distance(fwd_lst.begin(), fwd_lst.end());  // Calculate size manually.
```

<br>

---

<br>

## Other Operations

<br>

### remove(const T& value)

**Description:** Removes all elements with the given value.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
fwd_lst.remove(3);  // Removes all elements with the value 3.
```

<br>

### remove_if(UnaryPredicate p)

**Description:** Removes all elements that satisfy a predicate.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
fwd_lst.remove_if([](int x) { return x % 2 == 0; });  // Removes all even elements.
```

<br>

### reverse()

**Description:** Reverses the order of elements in the forward list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
fwd_lst.reverse();  // Reverses the order of the elements.
```

<br>

---

<br>

## Sorting and Merging

<br>

### sort()

**Description:** Sorts the elements in ascending order.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n log n) | O(1) |

```cpp
fwd_lst.sort();  // Sorts the forward list in ascending order.
```

<br>

### merge(std::forward_list& other)

**Description:** Merges two sorted forward lists into one sorted list.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::forward_list<int> fwd_lst2 = {1, 3, 5};
fwd_lst.merge(fwd_lst2);  // Merges fwd_lst2 into fwd_lst.
```

<br>

---

<br>

## Splice Operations

<br>

### splice_after(const_iterator pos, std::forward_list& other)

**Description:** Transfers elements from one forward list to another after the given position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) + O(n) (traversal) | O(1) |

```cpp
std::forward_list<int> fwd_lst2 = {50, 60, 70};
fwd_lst.splice_after(fwd_lst.begin(), fwd_lst2);  // Transfers all elements from fwd_lst2 to fwd_lst after the first element.
```

<br>

---

<br>

## Non-Member Functions

<br>

### swap

**Description:** Swaps the content of two forward lists.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::forward_list<int> fwd_lst2 = {9, 8, 7};
fwd_lst.swap(fwd_lst2);  // Swaps content of fwd_lst and fwd_lst2.
```

<br>

---

<br>

## Member Types

| Member Type        | Description                                    |
|--------------------|------------------------------------------------|
| `value_type`       | Type of elements in the forward list.           |
| `allocator_type`   | Allocator used to allocate memory.              |
| `size_type`        | Unsigned integer type representing the size.    |
| `difference_type`  | Signed integer type for pointer differences.    |
| `reference`        | Reference to `value_type`.                      |
| `const_reference`  | Constant reference to `value_type`.             |
| `pointer`          | Pointer to `value_type`.                        |
| `const_pointer`    | Constant pointer to `value_type`.               |
| `iterator`         | Forward iterator to `value_type`.               |
| `const_iterator`   | Constant forward iterator to `value_type`.      |