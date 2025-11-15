# Valid Anagram

Given two strings `s` and `t`. `t`, determine whether `t` is an anagram of `s`. Return `true` if they are anagrams, and `false` 

otherwise.An anagram is a word formed by rearranging the letters of another word, using all the original letters exactly once.

### Example 1:

```
Input: s = "god", t = "dog"
Output: true
```

### Example 2:

```
Input: s = "can", t = "pan"
Output: false
```

### Constraints:

- `s` and `t` consist of lowercase English letters.
- `1 <= s.length, t.length <= 4 * 10³`

```jsx
class Solution {
    /**
     * @param {string} s
     * @param {string} t
     * @return {boolean}
     */
    isAnagram(s, t) {
        // 1. Check Anagram should have same character length
        if(s.length !== t.length) {
            return false;
        }

        // 2. Create Map to mapping total of each character  
        const charCount = new Map();
        
        // 3. Iterate s as char
        for(const char of s) {
            // 4. Store every character into map, increment the count of character, if new default is 0 and then add 1
            charCount.set(char, (charCount.get(char) || 0) + 1);
        }

        // 5. Iterate t sa char
        for(const char of t) {
            // 6. create const count to get total character in previous variable for checking
            const count = charCount.get(char);
            
            // 7. Check if character t isn't on s or count is zero it mean the t !== s
            if(!count || count === 0) {
                return false;
            }

            // 8. Decrement count for future checking
            charCount.set(char, count - 1);
        }

        return true;

    }
}
```

# Detail Explanation

---

## 🧐 The Concept of Anagrams

First, let's confirm the definition: two strings are anagrams if one can be formed by rearranging the letters of the other, meaning they must have the **exact same characters** with the **exact same count** for each character.

For example, "listen" and "silent" are anagrams because both contain: one 'l', one 'i', one 's', one 't', one 'e', and one 'n'.

---

## 🚀 Optimal Solution: Frequency Counter

The most efficient way to check for anagrams is to use a **Frequency Counter** (a Map or object in JavaScript) to track the quantity of each character in both strings.

### Why this is Better than Sorting ($O(n \log n)$)

A common, less efficient solution is to sort both strings (e.g., `"god"` becomes `"dgo"`, `"dog"` becomes `"dgo"`) and check if the sorted strings are equal.

- **Sorting Time Complexity:** $O(n \log n)$, where $n$ is the string length.
- **Frequency Counter Time Complexity:** **$O(n)$** (Linear time).

Since $O(n)$ is faster than $O(n \log n)$ for large inputs, the frequency counter is the optimal approach.

---

## 🛠️ Step-by-Step Breakdown

We use a single `Map` to manage the counts for both strings in a two-pass process:

### Step 1: Initial Length Check (Prerequisite)

An immediate shortcut: if two strings have different lengths, they cannot be anagrams.

JavaScript

`if (s.length !== t.length) {
    return false;
}`

### Step 2: First Pass - Counting String $s$

We iterate through the first string (`s`) and use the `charCounts` Map to **record how many times each character appears**.

- **Action:** For every character in `s`, we **increment** its count in the Map.

**Example: `s = "god"`**

1. `'g'`: Count becomes 1. `charCounts = {'g': 1}`
2. `'o'`: Count becomes 1. `charCounts = {'g': 1, 'o': 1}`
3. `'d'`: Count becomes 1. `charCounts = {'g': 1, 'o': 1, 'd': 1}`

### Step 3: Second Pass - Checking String $t$

We now iterate through the second string (`t`). Instead of adding its characters to a separate map, we use `t` to **reduce the counts** stored from `s`.

- **Action:** For every character in `t`, we **decrement** its count in the Map.

**Example: `t = "dog"` (Starting Map: `{'g': 1, 'o': 1, 'd': 1}`)**

1. `'d'`: Check Map for 'd'. Count is 1. **Decrement** it.
    - `charCounts` becomes `{'g': 1, 'o': 1, 'd': 0}`
2. `'o'`: Check Map for 'o'. Count is 1. **Decrement** it.
    - `charCounts` becomes `{'g': 1, 'o': 0, 'd': 0}`
3. `'g'`: Check Map for 'g'. Count is 1. **Decrement** it.
    - `charCounts` becomes `{'g': 0, 'o': 0, 'd': 0}`

### The Failure Condition (The Shortcut)

During this second pass, if we encounter a character in `t` that:

1. **Is not in the Map at all** (meaning it wasn't in `s`).
2. **Has a count of 0** (meaning `t` has more instances of this character than `s`).

...then we know they can't be anagrams, and we immediately return `false`.

**Example: `t = "pan"` (If `s = "can"`)**

1. `s` creates Map: `{'c': 1, 'a': 1, 'n': 1}`
2. Process `'p'` from `t`: The character `'p'` is **not in the Map**. **Return `false`** instantly.

### Step 4: Final Result

If the program successfully completes the second pass without returning `false` (meaning the lengths were equal, and every character in `t` had a corresponding, unused count in `s`), it means the frequency of all characters must be exactly zero. Therefore, we **return `true`**.

---

## 📈 Summary of Efficiency

| **Metric** | **Detail** | **Result** |
| --- | --- | --- |
| **Time Complexity** | Iterate $s$ ($O(n$) + Iterate $t$ ($O(n)$) | **$O(n)$** |
| **Space Complexity** | Max 26 characters (lowercase English alphabet) | **$O(1)$** (Constant) |

This makes the frequency counter method the most desirable way to solve the Valid Anagram problem.