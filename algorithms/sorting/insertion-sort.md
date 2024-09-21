Insertion Sort is a basic sorting algorithm that incrementally builds a sorted section of the array by comparing and inserting elements into the correct position. It is intuitive but not efficient for large datasets due to its $O(n^2)$ complexity.

<br>

---

<br>

## Code Implementation

| Complexity     | Best Case   | Worst Case | Average Case | Space Complexity |
|----------------|-------------|------------|--------------|------------------|
| Time           | $O(n)$        | $O(n^2)$      | $O(n^2$)        | $O(1)$             |

```cpp
void insertionSort(std::vector<int>& arr) {
    for (size_t i = 1; i < arr.size(); i++) {
        int j = i - 1;
        while (j >= 0 && arr[j + 1] < arr[j]) {
            std::swap(arr[j], arr[j + 1]);
            j--;
        }
    }
}
```

<br>

---

<br>

### Line-by-Line Breakdown

<br>

```cpp
for (size_t i = 1; i < arr.size(); i++) {
```

> - **Outer loop**: Starts from the second element (`i = 1`) since the first element is considered trivially sorted. 
> - **Condition**: Loop continues as long as `i` is less than the size of the array.
> - **Purpose**: Each iteration inserts the element at index `i` into its correct position in the sorted subarray `arr[0...i-1]`.
> - **Reason for using size_t**: `size_t` is an unsigned integer type commonly used for array indexing and loop counters because it is guaranteed to be large enough to represent the size of any object, such as the length of a vector.

<br>


<br>

```cpp
int j = i - 1;
```

> - Initializes `j` to point to the element just before the current element (`arr[i]`).
> - `j` is used to compare and shift elements in the sorted part of the array to make space for the current element.

<br>

```cpp
while (j >= 0 && arr[j + 1] < arr[j]) {
```
> - **Condition**: The loop continues as long as:
> 	- `j >= 0` ensures we are not out of bounds.
> 	- `arr[j + 1] < arr[j]` checks if the current element (`arr[j + 1]`) is smaller than the previous element (`arr[j]`).
> - **Purpose**: Finds the correct position for the element being inserted by shifting larger elements to the right.

<br>

```cpp
std::swap(arr[j], arr[j + 1]);
```

> - Swaps `arr[j]` and `arr[j + 1]` to move the smaller element (`arr[j + 1]`) to the left.
> - The swap helps shift larger elements to the right, making room for the smaller element.

<br>

```cpp
j--;
```

> - Moves the pointer `j` one step left to continue checking and shifting elements in the sorted subarray.
> - **Purpose**: Keeps comparing until the correct insertion position is found or the start of the array is reached.

<br>

---

<br>

## Summary

Insertion Sort iterates through each element, shifting larger elements to the right until the current element can be inserted in its correct position. The algorithm has a time complexity of $O(n^2)$ in the worst case but performs well for small or nearly sorted datasets.