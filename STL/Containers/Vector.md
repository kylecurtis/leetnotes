`std::vector` is a sequence container representing arrays that can dynamically resize. Elements are stored contiguously, allowing random access and efficient addition/removal of elements at the end.

<br>

---

<br>

## Header File

To use `std::vector`, you need to include the following header:

```cpp
#include <vector>
```

<br>

---

<br>

## Time/Space Complexities Summary

| Function               | Time Complexity | Space Complexity |
|------------------------|-----------------|------------------|
| Constructor (default)   | O(1)            | O(1)             |
| Constructor (size)      | O(n)            | O(n)             |
| size()                 | O(1)            | O(1)             |
| capacity()             | O(1)            | O(1)             |
| push_back()            | O(1) amortized  | O(n)             |
| pop_back()             | O(1)            | O(1)             |
| insert()               | O(n)            | O(n)             |
| erase()                | O(n)            | O(1)             |
| clear()                | O(n)            | O(1)             |
| shrink_to_fit()        | O(n)            | O(1)             |
| begin()/end()          | O(1)            | O(1)             |
| swap()                 | O(1)            | O(1)             |

<br>

---

<br>

## Constructor

<br>

### std::vector()

**Description:** Creates an empty vector.

**Template Syntax:**

```cpp
std::vector<data_type> vector_name;
```

- `data_type`: The type of elements stored in the vector.
- `vector_name`: The name of the vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v;
```

<br>

### std::vector(size_type count)

**Description:** Creates a vector with `count` default-initialized elements (i.e., elements are initialized with their default value, such as `0` for `int`).

**Template Syntax:**

```cpp
std::vector<data_type> vector_name(count);
```

- `data_type`: The type of elements stored in the vector.
- `vector_name`: The name of the vector.
- `count`: The number of elements to create in the vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::vector<int> v(10);  // Creates a vector with 10 default-initialized elements.
```

<br>

### std::vector(size_type count, const T& value)

**Description:** Creates a vector with `count` elements, each initialized to `value`.

**Template Syntax:**

```cpp
std::vector<data_type> vector_name(count, value);
```

- `data_type`: The type of elements stored in the vector.
- `vector_name`: The name of the vector.
- `count`: The number of elements to create in the vector.
- `value`: The value to assign to each element.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::vector<int> v(10, 5);  // Creates a vector with 10 elements, all initialized to 5.
```

<br>

### std::vector(std::initializer_list<T> init)

**Description:** Creates a vector initialized with elements from an initializer list.

**Template Syntax:**

```cpp
std::vector<data_type> vector_name = {value1, value2, value3, ...};
```

- `data_type`: The type of elements stored in the vector.
- `vector_name`: The name of the vector.
- `value1, value2, value3, ...`: The values to initialize the vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::vector<int> v = {1, 2, 3};  // Creates a vector with the elements 1, 2, and 3.
```

<br>

---

<br>

## Capacity Functions

<br>

### size()

**Description:** Returns the number of elements in the vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
size_t s = v.size(); // s = 3
```

<br>

### capacity()

**Description:** Returns the number of elements that the vector can hold without reallocating.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
size_t c = v.capacity();
```

<br>

### reserve(size_type new_cap)

**Description:** Reserves storage for at least `new_cap` elements, avoiding frequent reallocations.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::vector<int> v;
v.reserve(100);  // Reserves memory for 100 elements.
```

<br>

### shrink_to_fit()

**Description:** Reduces the capacity to fit the size, freeing unused memory.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
v.shrink_to_fit();  // Reduces capacity to match size.
```

<br>

### empty()

**Description:** Checks if the vector contains no elements.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v;
bool is_empty = v.empty(); // true
```

<br>

---

<br>

## Element Access

<br>

### operator[] (subscript)

**Description:** Accesses the element at index `i`. No bounds checking.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
int x = v[1]; // x = 2
```

<br>

### at(size_type pos)

**Description:** Accesses the element at index `pos` with bounds checking.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
int x = v.at(1); // x = 2
```

<br>

### front()

**Description:** Returns the first element in the vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
int x = v.front(); // x = 1
```

<br>

### back()

**Description:** Returns the last element in the vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
int x = v.back(); // x = 3
```

<br>

---

<br>

## Modifiers

<br>

### push_back(const T& value)

**Description:** Adds an element to the end of the vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) (amortized) | O(n) |

```cpp
std::vector<int> v;
v.push_back(4);  // Adds 4 to the end of the vector.
```

<br>

### pop_back()

**Description:** Removes the last element in the vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
v.pop_back(); // v becomes {1, 2}
```

<br>

### insert(iterator pos, const T& value)

**Description:** Inserts `value` before the element at the given position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(n) |

```cpp
std::vector<int> v = {1, 2, 3};
v.insert(v.begin() + 1, 5); // v becomes {1, 5, 2, 3}
```

<br>

### erase(iterator pos)

**Description:** Erases the element at the given position.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
v.erase(v.begin() + 1); // v becomes {1

, 3}
```

<br>

### clear()

**Description:** Clears all elements from the vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
v.clear(); // v becomes {}
```

<br>

---

<br>

## Iterators

<br>

### begin()

**Description:** Returns an iterator to the first element.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
auto it = v.begin();
```

<br>

### end()

**Description:** Returns an iterator to the element following the last element.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
auto it = v.end();
```

<br>

### rbegin()

**Description:** Returns a reverse iterator to the first element of the reversed vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
auto rit = v.rbegin();
```

<br>

### rend()

**Description:** Returns a reverse iterator to the element following the last element of the reversed vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v = {1, 2, 3};
auto rit = v.rend();
```

<br>

---

<br>

## Special Functions

<br>

### swap(std::vector<T>& other)

**Description:** Swaps the contents of two vectors.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v1 = {1, 2, 3};
std::vector<int> v2 = {4, 5, 6};
v1.swap(v2); // v1 becomes {4, 5, 6}, v2 becomes {1, 2, 3}
```

<br>

### get_allocator()

**Description:** Returns the allocator associated with the vector.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

```cpp
std::vector<int> v;
auto alloc = v.get_allocator();
```

<br>

---

<br>

## Iterator Invalidation

**Description:** Some operations invalidate iterators. Here is a summary of when this occurs:

| Operation          | Invalidated Iterators           |
|--------------------|---------------------------------|
| `push_back()`       | If capacity changes, all iterators are invalidated. Otherwise, only `end()` is invalidated. |
| `insert()`         | Iterators from the point of insertion onwards are invalidated. |
| `erase()`          | Erased elements and iterators after them are invalidated. |
| `clear()`          | All iterators are invalidated. |
| `swap()`           | `end()` is invalidated. |

<br>

---

<br>

## Member Types

| Member Type        | Description                                    |
|--------------------|------------------------------------------------|
| `value_type`       | Type of elements in the vector (`T`).           |
| `allocator_type`   | The allocator used to allocate memory.          |
| `size_type`        | Unsigned integer type representing the size.    |
| `difference_type`  | Signed integer type for pointer differences.    |
| `iterator`         | A random-access iterator to `value_type`.       |
| `const_iterator`   | A random-access iterator to `const value_type`. |

<br>

---

<br>

## Non-Member Functions

<br>

### operator ==

**Description:** Lexicographically compares two vectors for equality.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

### operator <=>

**Description:** Compares vectors using the three-way comparison operator.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(n) | O(1) |

### std::swap

**Description:** Specializes `std::swap` for vectors.

| Time Complexity | Space Complexity |
| :--: | :---: |
| O(1) | O(1) |

<br>

---

<br>

## Specialization for `vector<bool>`

**Description:** A space-efficient specialization of `std::vector` that stores `bool` values as bits, significantly reducing memory usage.
