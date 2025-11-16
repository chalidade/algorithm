# Move Zeroes to End While Maintaining Order

Given an integer array nums, move all 0's to the end of it while maintaining  the relative order of the non-zero elements. The operation must be performed in-place without making a copy of the array.

### Example 1:

```
Input:{"nums":[0,1,0,3,12]}
Output:[1,3,12,0,0]
```

### Example 2:

```
Input:{"nums":[0,0,1]}
Output:[1,0,0]
```

### Constraints:

- `1 <= nums.length <= 10^4`
- `2^31 <= nums[i] <= 2^31 - 1`

---

# Code Solution

## Solution 1

```jsx
class Solution {
    /**
     * @param {number[]} nums
     * @return {void} Do not return anything, modify nums in-place instead.
     */
    moveZeroes(nums) {
        // 1. Create pointer as index
        let pointer = 0;

        // 2. Itterate nums
        for(let i = 0; i < nums.length; i++) {
            
            // 3. Crate condition if nums[i] not 0, then move it's number to array base on index pointer
            if(nums[i] !== 0) {
                nums[pointer] = nums[i];
                pointer++;
            }
        }

        // 4. Because value zero has replaced, then we create condition to add 0 in the last of array until has same length 
        while(pointer < nums.length) {
            nums[pointer] = 0;
            pointer++;
        }
    }
}
```

## **Solution 2**

```jsx
const moveZeroesOptimized = (nums) => {
    let writePointer = 0;

    for (let i = 0; i < nums.length; i++) {
        // If the current element (read at i) is non-zero
        if (nums[i] !== 0) {
            // If the element is already at its correct place (i == writePointer), 
            // the swap does nothing, which is fine.
            if (i !== writePointer) {
                // Swap the non-zero element at 'i' with the element at 'writePointer' 
                // (which is currently a zero that we need to move).
                [nums[writePointer], nums[i]] = [nums[i], nums[writePointer]];
            }
            // Advance the writePointer to the next slot where a non-zero element should go.
            writePointer++;
        }
    }
};
```

---

Certainly. The "Move Zeroes" problem is a classic interview question designed to test your ability to perform an operation **in-place** (without creating a new array) with optimal **$O(n)$** time complexity.

I will detail the logic behind the most straightforward and effective method: the **Two-Pointer, Two-Pass** approach.

---

## 🧐 Detailed Explanation: Two-Pointer (Two-Pass) Method

The goal is to rearrange the array so that all non-zero numbers come first, in their original relative order, followed by all the zeros.

### Key Concept: The `writePointer`

We use a single pointer, which I call the `writePointer`, to track the position where the **next non-zero element should be written.**

- Initially, `writePointer` starts at index 0.

### Phase 1: Moving Non-Zeroes to the Front

We iterate through the entire array using the standard loop index, `i`, which acts as the **read pointer**.

The logic inside this loop is:

1. **Read an element:** Look at `nums[i]`.
2. **Check if it is a non-zero element:**
    - **If `nums[i]` is NON-ZERO:** This number belongs in the non-zero section at the front. We copy `nums[i]` into the spot designated by the `writePointer` (`nums[writePointer] = nums[i]`). Then, we immediately move the `writePointer` forward one step to mark the next empty spot for a non-zero number.
    - **If `nums[i]` is ZERO:** We do nothing. We let the read pointer (`i`) move forward. **Crucially, the zero remains in its spot for now, but the `writePointer` does not move.** This means the `writePointer` holds the position that this zero will eventually be overwritten by a later non-zero number, or will be filled by the second pass.

### Example Walkthrough (Phase 1)

Input: `nums = [0, 1, 0, 3, 12]`

| **i (Read)** | **nums[i]** | **Action (nums[i] !== 0)** | **nums (Array State)** | **writePointer** |
| --- | --- | --- | --- | --- |
| 0 | 0 | Do Nothing (Zero) | `[0, 1, 0, 3, 12]` | 0 |
| 1 | **1** | Copy `1` to `nums[0]`. Incr. pointer. | `[1, 1, 0, 3, 12]` | 1 |
| 2 | 0 | Do Nothing (Zero) | `[1, 1, 0, 3, 12]` | 1 |
| 3 | **3** | Copy `3` to `nums[1]`. Incr. pointer. | `[1, 3, 0, 3, 12]` | 2 |
| 4 | **12** | Copy `12` to `nums[2]`. Incr. pointer. | `[1, 3, 12, 3, 12]` | 3 |

**End of Phase 1:** The non-zero elements are correctly positioned and in order: `[1, 3, 12, ...]` The `writePointer` is now at index 3.

### Phase 2: Filling the Remainder with Zeroes

After Phase 1 finishes, the `writePointer` points to the *first position* that needs to be filled with a zero. All elements from this index to the end of the array must be zeroes.

- We start a simple loop (a `while` loop is cleanest) from the current `writePointer` position up to the end of the array.
- In each iteration, we set `nums[writePointer]` to `0` and advance the pointer.

### Example Walkthrough (Phase 2)

Start state: `nums = [1, 3, 12, 3, 12]`, `writePointer = 3`

| **writePointer** | **Array Index** | **Action** | **nums (Array State)** |
| --- | --- | --- | --- |
| 3 | 3 | Set `nums[3] = 0` | `[1, 3, 12, 0, 12]` |
| 4 | 4 | Set `nums[4] = 0` | `[1, 3, 12, 0, 0]` |
| 5 | End | Stop | `[1, 3, 12, 0, 0]` |

**Final Result:** `[1, 3, 12, 0, 0]`.

### Summary of Efficiency

This method is optimal because it achieves:

- **$O(n)$ Time Complexity:** We only read and write to the array a maximum of two times (once in Phase 1 and once in Phase 2, which is $O(n) + O(n) = O(n)$).
- **$O(1)$ Space Complexity:** We only use a single extra variable (`writePointer`) for bookkeeping, meeting the "in-place" requirement without auxiliary storage.