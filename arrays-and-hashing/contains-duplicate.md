# Contains Duplicate

Given an integer array **`nums`**, determine whether any element appears **more than once**. Return **`true`** if a duplicate exists, and `false` otherwise.

### Example 1:

```
Input: nums = [1, 1, 2, 3]
Output: true
```

### Example 2:

```
Input: nums = [1, 2, 3, 4]
Output: false
```

### Constraints:

- `2 <= nums.length <= 10³`
- `−10⁷ <= nums[i] <= 10⁷`

### Interview Recommendation:

- Aim to create a solution that has `O(n)` time and space complexity

---

# Code Solution

## Solution 1

```jsx
class Solution {
    /**
     * @param {number[]} nums
     * @return {boolean}
     */
    hasDuplicate(nums) {
        // 1. Create map to store num and value
        const countNum = new Map();
				
				// 2. Iterate array num
        for(const num of nums) {
		        // 3. create variable count for checking 
            const count = countNum.get(num);
            
            // 4. check if is count more than one it means duplicate
            if(count > 0) {
                return true;
            }
						
						// 5. save count each number
            countNum.set(num, (countNum.get(num) || 0) + 1);

        } 
				
				// 6. No duplicate
        return false;
    }
}
```

## Solution 2

```jsx
class Solution {
    /**
     * @param {number[]} nums
     * @return {boolean}
     */
    hasDuplicate(nums) {
        // 1. Use Set to track unique numbers
        const hasSeen = new Set();
        
        // 2. iterate nums as num
        for (const num of nums) {
		        // 3. if num has seen or has stored, it mean duplicate 
            if (hasSeen.has(num)) {
                return true;
            }
            
            // 4. if num new, then store to hasSeen variable
            hasSeen.add(num);
        }
        
        // 5. There no duplicate
        return false;
    }
}
```

## Solution 3

```jsx
class Solution {
    /**
     * @param {number[]} nums
     * @return {boolean}
     */
    hasDuplicate(nums) {
		    // Because Set always store unique value, we can simple check size between object Sets and nums. if it's different it mean there's duplicate number. 
        return new Set(nums).size < nums.length;
    }
}
```

---

# Detail Explanation

This problem, **"Contains Duplicate,"** asks you to determine if any element in an integer array `nums` appears more than once. We need to aim for an efficient solution with $O(n)$ time complexity.

The most efficient way to solve this is by using a **Hash Set** (or JavaScript `Set` object) to record the numbers we've already encountered.

## 🧠 Contains Duplicate Solution (JavaScript)

The **Set** is the perfect tool here because it only stores **unique values** and provides average $O(1)$ time complexity for adding elements and checking for existence (`add` and `has`).

JavaScript

```jsx
/**
 * @param {number[]} nums
 * @return {boolean}
 */
const containsDuplicate = (nums) => {
    // Initialize a Set to store the unique numbers encountered so far.
    const uniqueElements = new Set();

    // Iterate through the array once.
    for (const num of nums) {
        // 1. Check if the current number is already in the Set.
        // If it is, we've found a duplicate.
        if (uniqueElements.has(num)) {
            return true;
        }

        // 2. If it's not in the Set, add it.
        uniqueElements.add(num);
    }

    // If the loop finishes without returning true, no duplicates were found.
    return false;
};
```

---

## ⚙️ Complexity Analysis

The recommended complexity for interview problems like this is $O(n)$, and the Set approach achieves it.

### Time Complexity: $O(n)$

- We iterate through the array `nums` exactly once.
- The fundamental operations on a JavaScript `Set`—checking for existence (`has`) and insertion (`add`)—take an average of **$O(1)$** (constant time).
- Therefore, the total time complexity is dominated by the single pass through the array, resulting in **$O(n)$**.

### Space Complexity: $O(n)$

- In the worst-case scenario (e.g., if the array has no duplicates), the `Set` will store all $n$ elements from the input array.
- Thus, the space required grows linearly with the input size, resulting in **$O(n)$** space complexity.

---

## ✨ Alternative: The One-Liner (Functional Approach)

In JavaScript, you can achieve the same result concisely by comparing the length of the original array with the size of a new Set created from that array.

JavaScript

```jsx
const containsDuplicateOneLiner = (nums) => {
    // If the number of unique elements (Set size) is less than the total 
    // number of elements (array length), there must be duplicates.
    return new Set(nums).size < nums.length;
};
```

This functional approach still has the same $O(n)$ time and $O(n)$ space complexity because it requires iterating through the array once to build the Set.