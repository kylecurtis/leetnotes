
<br>

**Difficulty:** Easy  
**Topics:** Two Pointers, String

<br>

---

<br>

## Problem Description

<br>

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) with $O(1)$ extra memory.

<br>

**Example 1:**

> **Input:** `s = ["h","e","l","l","o"]`  
> **Output:** `["o","l","l","e","h"]`

<br>

**Example 2:**

> **Input:** `s = ["H","a","n","n","a","h"]`  
> **Output:** `["h","a","n","n","a","H"]`

<br>

**Constraints:**

- $1 \leq \text{s.length} \leq 10^5$
- `s[i]` is a [printable ascii character](https://en.wikipedia.org/wiki/ASCII#Printable_characters).

<br>

---

<br>

## Solution

### Time and Space Complexity

| Complexity | Value  |
|------------|--------|
| Time       | O(n)   |
| Space      | O(1)   |

### Code Implementation

```cpp
class Solution {
public:
    void reverseString(vector<char>& s) {
        int left = 0;
        int right = s.size() - 1;

        while (left < right) {
            swap(s[left], s[right]);
            left++;
            right--;
        }
    }
};
```

---

<br>

## Line-by-Line Code Breakdown

```cpp
int left = 0;
int right = s.size() - 1;
```

- **Explanation**:
  - The code defines two pointers:
    - `left` starts at index `0`, which represents the first character of the string.
    - `right` starts at the last index `s.size() - 1`, representing the last character of the string.
  - These two pointers will move towards each other, swapping the characters they point to, until they meet in the middle.

<br>

```cpp
while (left < right) {
```

- **Explanation**:
  - This `while` loop continues as long as `left` is less than `right`, meaning there are still characters to swap between the front and the back of the string.
  - When `left` becomes equal to or greater than `right`, the loop stops because the string has been reversed.

<br>

```cpp
swap(s[left], s[right]);
```

- **Explanation**:
  - This line swaps the characters at indices `left` and `right`.
  - The `swap()` function exchanges the values of `s[left]` and `s[right]`, effectively moving the character from the start of the string to the end, and vice versa.

<br>

```cpp
left++;
right--;
```

- **Explanation**:
  - After swapping, the `left` pointer is incremented to move one step to the right, and the `right` pointer is decremented to move one step to the left.
  - This ensures that in the next iteration, we will be swapping the next pair of characters from the start and the end of the string.

<br>

---

<br>

## Conclusion

This solution efficiently reverses the input string using the **two-pointer technique**. The two pointers move towards the center of the string, swapping the characters in-place without using extra memory.

### Time Complexity:
- **O(n)**: The loop iterates through half of the string (i.e., $n/2$ iterations), but this simplifies to O(n).

### Space Complexity:
- **O(1)**: The algorithm uses a constant amount of extra space, since the reversal happens in-place without requiring additional storage proportional to the input size.

This approach is optimal and works well for large strings with up to $10^5$ characters, as required by the problem constraints.