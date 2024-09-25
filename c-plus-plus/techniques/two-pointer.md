The **two-pointer technique** is an efficient way to solve array or list problems by using two variables (or "pointers") that traverse the data structure at the same time, either from opposite ends or from the same starting point. This approach often reduces the time complexity compared to using nested loops.

<br>

---

<br>

### When to Use:

- **Sorted Arrays**: Useful when working with sorted arrays to find pairs or subarrays.
- **Search Problems**: Efficient for finding specific patterns or relationships in arrays.
- **Minimizing Time Complexity**: Frequently reduces $O(n^2)$ problems to $O(n)$.

<br>

---

<br>

## Types of Two-Pointer Approaches

<br>

1. **Opposite Directions**  
   Two pointers start at different ends of the array (e.g., one at the start and one at the end) and move toward each other. This is common for problems where you need to compare elements from both sides.
   
   - **Common Use**: Finding pairs that satisfy a condition, like a target sum.

<br>

2. **Same Direction**  
   Both pointers start at the same point (usually the beginning) and move together, though one may move faster than the other. This is used in scenarios where one pointer represents the start of a range and the other represents the end.

   - **Common Use**: Sliding windows, subarray problems, or finding ranges that satisfy a condition.

<br>

---

<br>

## Basic Example: Finding a Pair with Target Sum (Sorted Array)

<br>

### Explanation:

1. Initialize two pointers: 
   - `left` at the start.
   - `right` at the end.
2. Compare the sum of `arr[left]` and `arr[right]` to the target:
   - If the sum is equal, you've found a solution.
   - If the sum is too small, move the `left` pointer to the right.
   - If the sum is too large, move the `right` pointer to the left.
3. Stop when the pointers cross.

<br>

### Simple C++ Code:

```cpp
#include <vector>
#include <iostream>

void findPairWithSum(const std::vector<int>& arr, int target) {
    int left = 0;
    int right = arr.size() - 1;

    while (left < right) {
        int sum = arr[left] + arr[right];
        
        if (sum == target) {
            std::cout << "Pair found: " << arr[left] << " and " << arr[right] << '\n';
            return;
        } else if (sum < target) {
            left++; // Move left pointer right to increase the sum
        } else {
            right--; // Move right pointer left to decrease the sum
        }
    }

    std::cout << "No pair found." << '\n';
}
```

<br>

### Explanation:
- `left` and `right` are initialized at the beginning and end of the array.
- The while loop runs until `left` meets `right`.
- Based on the sum, the pointers move to explore other pairs.

<br>

---

<br>

## Opposite Direction Example: Reversing an Array

<br>

### Explanation:
1. Initialize two pointers:
   - `left` at the start.
   - `right` at the end.
2. Swap elements at `left` and `right`.
3. Move the `left` pointer to the right and the `right` pointer to the left.
4. Stop when the pointers cross.

<br>

### Simple C++ Code:
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

void reverseArray(std::vector<int>& arr) {
    int left = 0;
    int right = arr.size() - 1;

    while (left < right) {
        std::swap(arr[left], arr[right]); // Swap elements
        left++; // Move left pointer right
        right--; // Move right pointer left
    }
}

int main() {
    std::vector<int> arr = {1, 2, 3, 4, 5};
    reverseArray(arr);

    for (int num : arr) {
        std::cout << num << " "; // Output: 5 4 3 2 1
    }
}
```

<br>

### Explanation:
- This demonstrates how two pointers can be used to reverse an array by swapping elements from the beginning and end.
- The two pointers meet in the middle, at which point the array is reversed.

<br>

---

<br>

## Same Direction Example: Removing Duplicates from Sorted Array

<br>

### Explanation:

1. Use two pointers that start at the beginning.
   - `slow` pointer tracks the position of the last unique element.
   - `fast` pointer iterates over the array to find the next unique element.
2. When a new unique element is found, move it to the `slow` pointer's position.
3. Continue until the entire array is processed.

<br>

### Simple C++ Code:
```cpp
#include <iostream>
#include <vector>

int removeDuplicates(std::vector<int>& arr) {
    if (arr.empty()) return 0;

    int slow = 0; // Pointer for unique elements

    for (int fast = 1; fast < arr.size(); fast++) {
        if (arr[fast] != arr[slow]) {
            slow++; // Move slow pointer
            arr[slow] = arr[fast]; // Copy unique element to the slow pointer
        }
    }

    return slow + 1; // Length of unique elements
}

int main() {
    std::vector<int> arr = {1, 1, 2, 2, 3, 3};
    int newLength = removeDuplicates(arr);

    for (int i = 0; i < newLength; i++) {
        std::cout << arr[i] << " "; // Output: 1 2 3
    }
}
```

<br>

### Explanation:
- `slow` pointer tracks the position where unique elements should go.
- `fast` pointer checks the rest of the array for new unique elements.
- The technique avoids the need for a new array and works in-place.

<br>

---

<br>

## General Steps for Using Two-Pointer Technique:

<br>

1. **Initialize** the pointers:
   - Either at the beginning and end, or both at the start.
2. **Move the pointers**:
   - Decide how to move the pointers based on the problem (e.g., one pointer moves left, the other moves right, or both move in the same direction).
3. **Stop condition**:
   - Determine when the pointers should stop (e.g., when they meet, when a condition is satisfied).
4. **Process the data**:
   - Depending on the problem, pointers might swap elements, sum values, or track ranges.

<br>

---

<br>

## Key Takeaways:

- The two-pointer technique is very versatile and often used to reduce time complexity.
- It works best with sorted data but can also be adapted for other types of problems.
- Always carefully plan when and how to move the pointers, depending on the problem constraints.