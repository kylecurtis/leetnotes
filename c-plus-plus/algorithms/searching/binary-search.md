Binary Search is an efficient algorithm for finding the position of a target value within a sorted array. The algorithm works by repeatedly dividing the search interval in half. If the target value is greater than the middle element, the search continues in the upper half; otherwise, it searches in the lower half. This results in a logarithmic time complexity of $O(\log n)$.

<br>

---

<br>

## Code Implementation

| Complexity     | Best Case   | Worst Case | Average Case | Space Complexity |
|----------------|-------------|------------|--------------|------------------|
| Time           | $O(1)$        | $O(\log n)$      | $O(\log n)$        | $O(1)$             |

```cpp
int binarySearch(const std::vector<int>& arr, int target) {
    int L = 0, R = arr.size() - 1;

    while (L <= R) {
        int mid = L + (R - L) / 2;

        if (target > arr[mid]) {
            L = mid + 1;
        } else if (target < arr[mid]) {
            R = mid - 1;
        } else {
            return mid;
        }
    }
    return -1;
}
```

<br>

---

<br>

### Line-by-Line Breakdown

<br>

```cpp
int L = 0, R = arr.size() - 1;
```

> - **L (Left)**: This initializes `L` to the starting index of the array (0).
> - **R (Right)**: This initializes `R` to the last index of the array (`arr.size() - 1`).
> - **Purpose**: These two variables define the boundaries of the search range, which is initially the entire array.

<br>

```cpp
while (L <= R) {
```

> - **Condition**: The loop runs as long as the left index (`L`) is less than or equal to the right index (`R`), meaning there is still a valid search range.
> - **Purpose**: This loop performs the binary search by continuously narrowing down the search range.

<br>

```cpp
int mid = L + (R - L) / 2;
```

> - **Midpoint Calculation**: Calculates the middle index of the current search range.
> - **Reason for `L + (R - L) / 2`**: This prevents potential integer overflow that could occur if you directly used `(L + R) / 2` for very large values of `L` and `R`.
> - **Purpose**: `mid` represents the index of the middle element, which is used to decide which half of the array to search next.

<br>

```cpp
if (target > arr[mid]) {
    L = mid + 1;
}
```

> - **Condition**: If the target is greater than the middle element, the target must be in the right half of the array.
> - **Action**: Updates the left boundary (`L`) to `mid + 1`, effectively discarding the left half of the current search range.

<br>

```cpp
else if (target < arr[mid]) {
    R = mid - 1;
}
```

> - **Condition**: If the target is smaller than the middle element, the target must be in the left half of the array.
> - **Action**: Updates the right boundary (`R`) to `mid - 1`, discarding the right half of the current search range.

<br>

```cpp
else {
    return mid;
}
```

> - **Condition**: If the target is equal to the middle element, the search is successful.
> - **Action**: Returns the index `mid`, which is the position of the target in the array.

<br>

```cpp
return -1;
```

> - **Condition**: If the loop completes without finding the target, the function returns `-1`.
> - **Purpose**: This indicates that the target value is not present in the array.

<br>

---

<br>

## Summary

Binary Search is an efficient way to search for a target value in a sorted array. By repeatedly dividing the search space in half, it achieves a time complexity of $O(\log n)$. The algorithm performs well with large datasets but requires the array to be sorted before searching.