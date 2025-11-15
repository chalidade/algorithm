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

This repository grows continuously as I learn, revise, and solve real-world DSA challenges.

---

## 🧠 What’s Inside?
The learning path follows major DSA categories commonly used in interviews, competitive programming, and real-world development.

### 📂 Topics Covered  
Based on the repository structure:

```
📦 dsa-learning
 ┣ 📂 arrays-and-hashing
 ┣ 📂 binary-search
 ┣ 📂 bit-manipulation
 ┣ 📂 blind-75
 ┣ 📂 dynamic-programming
 ┣ 📂 graphs
 ┣ 📂 greedy
 ┣ 📂 heaps
 ┣ 📂 intervals
 ┣ 📂 linked-list
 ┣ 📂 math-and-geometry
 ┣ 📂 matrix
 ┣ 📂 queues
 ┣ 📂 recursion
 ┣ 📂 search-algorithm
 ┣ 📂 sliding-window
 ┣ 📂 sorting-algorithm
 ┣ 📂 stacks
 ┣ 📂 tech-preparation
 ┣ 📂 trees
 ┣ 📂 tries
 ┣ 📂 two-pointers
 ┗ 📄 README.md
```

Each topic includes:  
- 📝 Explanation  
- 🧩 Problem-solving patterns  
- 💡 Code implementations  
- 🏹 Practice questions  

---

## 🧩 Example Code Snippet  

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
- Build a consistent coding practice habit  

---

## 🚀 About Me  
**Chalid Ade Rahman**  
Senior Front-End Developer • API & Scalable Web App Specialist  
5+ Years Remote Experience in EdTech, Logistics, and Non-Profit  

---

## 📬 Contact  
Feel free to reach out for collaboration, discussion, or opportunities:

- **📍 Location:** East Java, Indonesia  
- **📞 Phone:** +6285784566522  
- **📧 Email:** chalidade@gmail.com  
- **🔗 LinkedIn:** https://linkedin.com/in/chalidaderahman  

---

## ☕ Support My Work  
If you'd like to support my learning journey or say thank you:

👉 **Buy me a coffee:** https://teer.id/chalidade  

Your support means a lot and helps me continue writing, learning, and sharing!

---

## ⭐ Support & Contribution  
If this repository helps you:  
- ⭐ **Star the repo**  
- 🔁 Submit PRs  
- 🐛 Open issues  

---

## 🏁 Final Words  
This repository reflects continuous learning and growth.  
Every folder, every problem, is a step toward mastery.

> **“Practice makes improvement — consistency makes mastery.”**
