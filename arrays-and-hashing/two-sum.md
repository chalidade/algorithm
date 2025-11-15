# Two Sum

> Given an integer array `nums` and an integer `target`, find indices `i` and `j` such that `nums[i] + nums[j] == target` and `i != j`.Assume that every input has exactly one pair of indices `i` and `j` that fulfill this condition.Return the pair of indices with the smaller index first.
> 

### Example 1:

```
Input: nums = [1, 2, 3, 4], target = 5
Output: [0, 3]

Explanation: nums[0] + nums[3] == 5, so we return [0, 3].
```

### Example 2:

```
Input: nums = [0, -1, 2, -3, 1], target = -2
Output: [1, 3]
```

### Constraints:

- `2 <= nums.length <= 10³`
- `−10⁷ <= nums[i] <= 10⁷`
- `−10⁷ <= target <= 10⁷`

```jsx
class Solution {
    /**
     * @param {number[]} nums Array of integers
     * @param {number} target Target sum to find
     * @return {number[]} Indices of the two numbers that add up to target
     */
    twoSum(nums, target) {
        // 1. Create map to mapping key value 
        const numMap = new Map();

        // 2. Iterate through data of array as index
        for(let i = 0; i < nums.length; i++) {
            // 3. Create const to get current number
            const currentNum = nums[i];

            // 4. Calculate the required complement
            const complement = target - currentNum;

            // 5. Check if complement has been seen on map
            if(numMap.has(complement)) {
                // 6. It's found 
                return [numMap.get(complement), i];
            }

            // 7. Store the current value and index for future lookup
            numMap.set(currentNum, i);
        }

        // 8. Is the problem not match with requirement, throw empty array
        return [];
        
    }
}
```

---

### **My Summary**

The flow to solve this exercise 

- Create **Map** to mapping value and index
- Then Iterate array as one way from left to right
- Get complement value using formulas **complement = target - current_number**
- Check is **complement value** has found in Map
- If yes, show **index** for **complement value** and **current index** because we iterate data from left to the right, **complement index** should always smaller than **current index**
- If the data / case not as the constraints or requirement return empty array

---

### Detailed Explanation of the Two Sum Solution

The core idea of the efficient solution for the Two Sum problem is the principle of **"Trading Search Time for Storage Space"** using a data structure called a **Hash Map** (or `Map` in JavaScript).

### 1. The Concept of the "Complement"

In any two-sum problem, if you are looking for two numbers that add up to a `target`, once you pick the first number, you know exactly what the second number must be. This required second number is called the **Complement**.

$$
Complement = Target − Current Number
$$

**Example:** If the `Target = 15` and the `Current Number = 9`, the Complement must be 15−9=6. You only need to check if the number **6** has been seen before.

### 2. The Role of the JavaScript `Map` (Hash Map)

A **Hash Map** (implemented as `Map` in JavaScript) is a data structure designed for extremely fast lookups. It stores data as key-value pairs (`{key: value}`).

In our Two Sum solution, the `Map` stores:

- **Key:** The number we have already encountered (`nums[i]`).
- **Value:** The index (position) of that number in the array (`i`).

### Key Advantage: O(1) Time Complexity

The most critical feature of a Hash Map is that operations like **checking if a key exists** (`map.has()`) and **retrieving a value** (`map.get()`) take **Constant Time** (Average **O(1)**).

This means whether your array has 10 elements or 10 million, checking the map takes roughly the same, almost instantaneous, amount of time. This eliminates the need for a slow O(n) linear search inside a loop.

### 3. The Single-Pass O(n) Algorithm

By using the Map, we can solve the problem by iterating through the array just **once** (a single pass).

For each number (`currentNum`) at index `i`, we perform two steps:

### Step A: Check (Looking Backward)

1. Calculate the `complement` needed: `complement = target - currentNum`.
2. **Ask:** "Has this `complement` been stored in our `numMap` yet?" (i.e., `numMap.has(complement)`).

If the answer is **YES**:

- We have found the pair! The complement was encountered earlier (at a smaller index), and the `currentNum` is the second number (at the current index `i`).
- We immediately return the result: `[numMap.get(complement), i]`. **The search is complete.**

### Step B: Store (Preparing for the Future)

If the answer is **NO**:

1. The pair has not been found yet.
2. We **store** the `currentNum` and its index (`i`) into the map: `numMap.set(currentNum, i)`.
3. **Purpose:** This number is now available as a potential **Complement** for any numbers that appear **later** in the array.