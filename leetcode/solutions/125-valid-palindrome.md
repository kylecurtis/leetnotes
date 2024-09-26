<br>

**Difficulty:** Easy  
**Topics:** Two Pointers, String

<br>

---

<br>

## Problem Description

Given a string `s`, return _true if it is a palindrome, or false otherwise_.

A string is a palindrome if it reads the same forward and backward after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters.

<br>

**Example 1:**

> **Input:** `s = "A man, a plan, a canal: Panama"`  
> **Output:** `true`  
> **Explanation:** "amanaplanacanalpanama" is a palindrome.

<br>

**Example 2:**

> **Input:** `s = "race a car"`  
> **Output:** `false`  
> **Explanation:** "raceacar" is not a palindrome.

<br>

**Constraints:**

- $1 \leq \text{s.length} \leq 2 \times 10^5$
- `s` consists only of printable ASCII characters.

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
    bool isPalindrome(string s) {
        size_t left{0};
        size_t right{s.length() - 1};

        while (left < right) {
            if (!isalnum(s[left])) {
                left++;
            }
            else if (!isalnum(s[right])) {
                right--;
            }
            else {
                if (tolower(s[left++]) != tolower(s[right--])) {
                    return false;
                }
            }
        }
        return true;
    }
};
```

<br>

---

<br>

## Line-by-Line Code Breakdown

```cpp
size_t left{0};
size_t right{s.length() - 1};
```

- **Explanation**:
  - Initializes two pointers, `left` starting from the beginning of the string and `right` from the last index.
  - These pointers will move towards each other to check for palindrome conditions.

<br>

```cpp
while (left < right) {
```

- **Explanation**:
  - Starts a loop that runs as long as `left` is less than `right`. This means the two pointers haven't crossed, and characters still need to be checked.

<br>

```cpp
if (!isalnum(s[left])) {
    left++;
}
```

- **Explanation**:
  - If the character at `s[left]` is not alphanumeric, it is skipped by incrementing the `left` pointer.
  - Non-alphanumeric characters are ignored in the palindrome check.

<br>

```cpp
else if (!isalnum(s[right])) {
    right--;
}
```

- **Explanation**:
  - Similarly, if the character at `s[right]` is not alphanumeric, the `right` pointer is decremented to skip it.
  - This helps to focus only on the alphanumeric characters.

<br>

```cpp
else {
    if (tolower(s[left++]) != tolower(s[right--])) {
        return false;
    }
}
```

- **Explanation**:
  - Converts both `s[left]` and `s[right]` to lowercase for case-insensitive comparison.
  - If the characters don't match, it returns `false` immediately, indicating the string is not a palindrome.
  - If they match, both pointers are updated to continue checking the rest of the string.

<br>

```cpp
return true;
```

- **Explanation**:
  - If all characters match, the function returns `true`, confirming the string is a valid palindrome.

<br>

---

<br>

## Conclusion

This two-pointer approach efficiently checks if the given string is a palindrome by skipping non-alphanumeric characters and comparing alphanumeric ones in a case-insensitive manner. The algorithm runs in linear time, making it suitable for large strings up to $2 \times 10^5$ characters.
