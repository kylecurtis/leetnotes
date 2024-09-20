<br>

**Difficulty:** Easy  
**Topics:** Array, Hash Table

<br>

---

<br>

## Problem Description

<br>

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

<br>

**Example 1:**

> **Input:** nums = [2,7,11,15], target = 9
> **Output:** [0,1]
> **Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

<br>

**Example 2:**

> **Input:** nums = [3,2,4], target = 6
> **Output:** [1,2]

<br>

**Example 3:**

> **Input:** nums = [3,3], target = 6
> **Output:** [0,1]

<br>

**Constraints:**

- $2$ $\le$ `nums.length` $\le$ $104$
- $-10^9$ $\le$ `nums[i]` $\le$ $10^9$
- $-10^9$ $\le$ `target` $\le$ $10^9$
- **Only one valid answer exists.**

<br>

**Follow-up:** Can you come up with an algorithm that is less than `O(n2)` time complexity?

<br>

---

<br>

## Solution

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
		unordered_map<int, int> map;

		for (int i = 0; i < nums.size(); i++) {
			int complement = target - nums[i];

			// If the complement exists in the map, return the indices
			if (map.find(complement) != map.end()) {
				return {map[complement], i};
			}

			// Otherwise, add the current number and its index to the map
			map[nums[i]] = i;
		}

		// Return an empty vector if no solution is found (not expected in this problem)
		return {};
    }
};
```

<br>

---

<br>

## Solution Breakdown

Here is a step-by-step explanation of how the solution works:

### 1. **Understanding the Problem:**
   The problem asks us to find two numbers in the array `nums` that add up to a given `target`. Instead of finding the actual numbers, we need to return their indices.

   - We are guaranteed that **exactly one solution exists**, which means we don’t have to handle cases where there are no valid pairs.
   - The problem specifies that we cannot use the same element twice.

<br>

### 2. **Using a Hash Map for Fast Lookup:**
   To solve this problem efficiently, we can use a hash map (`unordered_map` in C++) to store the indices of the elements as we iterate through the array.

   - For each element `nums[i]`, we calculate its complement: `complement = target - nums[i]`.
   - We then check if this complement has already been added to the hash map (i.e., if there is an earlier element that can pair with `nums[i]` to sum up to `target`).
   - If it exists, we return the index of the complement and the current index `i`.
   - If it doesn’t exist, we add `nums[i]` and its index `i` to the map for future reference.

<br>

### 3. **Walkthrough of the Code:**

- **Step 1:** We initialize an empty hash map `map`, which will store each number and its corresponding index.
  
- **Step 2:** We loop through the array `nums` with an index `i`.
  
- **Step 3:** For each element `nums[i]`, we compute the complement as `target - nums[i]`.

- **Step 4:** If the complement is already in the hash map (i.e., we’ve encountered a number earlier that, when added to `nums[i]`, gives the target), we return the indices of the two numbers.

- **Step 5:** If the complement isn’t found, we store the current number `nums[i]` and its index `i` in the map, so we can refer to it later.

- **Step 6:** The loop continues until we find the solution. Since the problem guarantees that there’s exactly one solution, we won’t need to handle cases where no solution exists.

<br>

### 4. **Time Complexity Analysis:**

- **Time Complexity:**  
  The time complexity of the solution is $O(n)$, where `n` is the length of the array `nums`. Here's why:
  
  - We iterate through the array once (i.e., a single pass), which gives an $O(n)$ time complexity.
  - Lookup and insertion in a hash map (unordered_map in C++) both have an average time complexity of $O(1)$.

  Thus, the overall time complexity is $O(n)$.

<br>

### 5. **Space Complexity Analysis:**

- **Space Complexity:**  
  The space complexity is $O(n)$ because, in the worst case, we may need to store all `n` elements in the hash map.

  Specifically, the hash map stores each number and its corresponding index, so the space used grows linearly with the input size.

<br>

---

<br>

## Conclusion

This solution efficiently solves the Two Sum problem using a hash map, achieving a time complexity of $O(n)$ and space complexity of $O(n)$. It’s faster than a brute-force approach, which would involve checking all pairs and have a time complexity of $O(n^2)$.

By using a hash map, we reduce the time needed for finding the complement of each number, making this approach suitable for large input sizes (up to $10^4$ elements, as per the problem's constraints).