# 📚 Data Structures & Algorithms
*A curated collection of problem-solving patterns, algorithm implementations, and DSA learning notes.*

> **“An algorithm is a step-by-step procedure for solving a problem.”**  
> Think of it like a blueprint, a recipe, or a flowchart.  
>
> This repository contains all algorithms and data structures I’ve learned and practiced throughout my journey as a software engineer — documented to build strong fundamentals, sharpen problem-solving skills, and prepare for technical interviews.

---

## 🔥 Why This Repository?
As a software developer with experience building scalable systems and high-performance applications, problem-solving is at the core of my work. Strengthening Data Structures & Algorithms helps me:

- Write more efficient and optimized code  
- Improve system design & logical thinking  
- Solve technical interview problems  
- Build a strong engineering foundation  

This repo grows continuously as I learn, revise, and solve real-world DSA challenges.

---

## 🧠 What’s Inside?
The learning path follows major DSA categories commonly used in interviews, competitive programming, and real-world development.

### 📂 Topics Covered

| Category | Description |
|---------|-------------|
| **Arrays & Hashing** | 57 questions – fundamentals of data storage, hashing, and lookups |
| **Binary Search** | 3 questions – efficient searching on sorted structures |
| **Bit Manipulation** | 12 questions – optimization using binary operations |
| **Blind 75** | 75 essential interview problems |
| **Dynamic Programming** | 24 questions – optimal substructure & overlapping subproblems |
| **Graphs** | 52 questions – BFS, DFS, shortest path, cycles |
| **Greedy** | 5 questions – optimal local decisions |
| **Heaps** | 33 questions – min/max heap, priority queues |
| **Intervals** | 5 questions – merge, scheduling, overlapping intervals |
| **Linked Lists** | 31 questions – pointers, traversal, reversal |
| **Math & Geometry** | 9 questions – math-based algorithms |
| **Matrix** | 7 questions – grid-based problems |
| **Queues** | 17 questions – FIFO operations |
| **Recursion** | 15 questions – backtracking, divide & conquer |
| **Search Algorithms** | 23 questions – BFS, DFS exploration |
| **Sliding Window** | 5 questions – substring optimization |
| **Sorting Algorithms** | 18 questions – comparison, non-comparison sorts |
| **Stacks** | 34 questions – LIFO, parsing, monotonic stacks |
| **TechPrep 100** | 100 curated practice questions |
| **Trees** | 44 questions – traversals, BST, binary trees |
| **Tries** | 25 questions – prefix trees |
| **Two Pointers** | 6 questions – array pointer strategies |

---

## 🧩 Code Example

```ts
function twoSum(nums: number[], target: number): number[] {
  const map = new Map();

  for (let i = 0; i < nums.length; i++) {
    const diff = target - nums[i];

    if (map.has(diff)) {
      return [map.get(diff), i];
    }

    map.set(nums[i], i);
  }

  return [];
}
```

---

## 📈 Tech Stack Used
- **Languages:** JavaScript, TypeScript  
- **Tools:** Git, VSCode, Node.js  
- **Patterns:** Sliding Window, Recursion, Dynamic Programming, Graph Traversal, Greedy, Heap Optimization  

---

## 🎯 Goals of This Repository
- Strengthen core DSA fundamentals  
- Prepare for senior-level technical interviews  
- Improve problem-solving and logical thinking  
- Create a structured, shareable knowledge base  
- Build a habit of writing optimized and clean code  

---

## 🗂️ Repository Structure

```
📦 dsa-learning
 ┣ 📂 arrays-and-hashing
 ┣ 📂 binary-search
 ┣ 📂 dynamic-programming
 ┣ 📂 graphs
 ┣ 📂 heaps
 ┣ 📂 sliding-window
 ┣ 📂 trees
 ┣ 📂 tries
 ┣ 📂 recursion
 ┗ 📄 README.md
```

---

## 🚀 About Me
**Chalid Ade Rahman**  
Senior Front-End Developer | API & Scalable Web App Specialist  
5+ Years Remote Experience in EdTech, Logistics & Non-Profit  

- Expert in React.js, Next.js, TypeScript  
- Strong problem-solving mindset  
- Passionate about algorithms, optimization, and systems engineering  

---

## ⭐ Support & Contribution
If you find this repository helpful:

👍 **Star this repo** to support  
🔁 Pull requests are welcome  
🐛 Issues and improvements are open for discussion  

---

## 🏁 Final Words
This repository is a long-term learning journey.  
Every algorithm added represents growth, improvement, and consistency.

> **“Practice makes improvement — consistency makes mastery.”**
