# Bellman-Ford Algorithm Presentation README

**Presenters:** Jhymani Joseph & Edvin Benjamin
**Course:** 3013 Algorithms with Dr. Terry Griffin
**Topic:** Bellman-Ford Algorithm

---

## 📌 Overview

The **Bellman-Ford algorithm** is a single-source shortest path algorithm used on weighted graphs. Unlike Dijkstra’s algorithm, it can handle graphs **with negative edge weights** and can detect **negative weight cycles**, making it a powerful and flexible choice in certain graph problems.

---

## 📚 Historical Background

* **Alfonso Shimbel** (1955): Introduced the earliest version.
* **Richard Bellman** (1956) and **Lester Ford Jr.** (1958): Independently proposed the formal algorithm.
* **Edward F. Moore** (1959): Introduced a notable variation.
* Sometimes referred to as the **Bellman-Ford-Moore Algorithm**.

---

## ✅ Key Features

### Advantages

* Supports **negative weights**.
* **Detects negative cycles**.
* Simple to implement.
* Works with **directed or undirected** graphs.
* Early stopping improves efficiency.
* Ideal for **sparse** graphs (using edge list representation).

### Disadvantages

* **Time complexity**: `O(VE)` → slower than Dijkstra for dense graphs.
* High space usage for large graphs.
* Inefficient for graphs with many edges.

---

## ⚙️ Algorithm Steps

1. **Initialization**
   Set all vertex distances to ∞ except the source, which is 0.

2. **Edge Relaxation (V - 1 times)**
   For each edge (u → v):
   If `dist[u] + weight < dist[v]`, update `dist[v]`.

3. **Negative Cycle Check**
   If further updates are possible, a **negative cycle exists**.

4. **Output**
   Return shortest distances and paths if no negative cycle is found.

---

## 🧪 Working Example

Given graph:

```
A → B (3)  
A → C (4)  
C → B (-2)  
B → D (5)
```

**Iterations (V = 4, so 3 passes):**

* After 1st pass:
  `dist(A)=0, dist(B)=2, dist(C)=4, dist(D)=7`

* No changes in passes 2 & 3 → early convergence.

---

## 📊 Comparison Table

| Feature             | Bellman-Ford  | Dijkstra                 | Floyd-Warshall        |
| ------------------- | ------------- | ------------------------ | --------------------- |
| Purpose             | Single-source | Single-source            | All-pairs             |
| Negative Weights    | ✅ Yes         | ❌ No                     | ✅ Yes                 |
| Detects Neg. Cycles | ✅ Yes         | ❌ No                     | ✅ Yes                 |
| Graph Type          | Any           | Pos. weights only        | Best for dense graphs |
| Time Complexity     | `O(VE)`       | `O(V²)` / `O((V+E)logV)` | `O(V³)`               |
| Space Complexity    | `O(V)`        | `O(V)`                   | `O(V²)`               |

---

## 🌍 Real-World Applications

1. **GPS Navigation Systems**

   * Chooses best routes under changing traffic conditions.
   * Accounts for route delays (negative weights).

2. **Network Routing (e.g., RIP protocol)**

   * Finds optimal paths between nodes.
   * Adapts to link failures and congestion.

3. **Currency Exchange (Financial Trading)**

   * Detects arbitrage opportunities via negative cycles.
   * Models currencies as nodes and exchange rates as edges.

---

## 📝 Sample Test Questions

1. **What can Bellman-Ford do that Dijkstra cannot?**
   **Answer:** Detect negative weight cycles.

2. **What is the time complexity of Bellman-Ford?**
   **Answer:** `O(VE)`

3. **How many times are edges relaxed (without early stopping)?**
   **Answer:** `V - 1`

4. **What is the update process called?**
   **Answer:** Relaxation

---

## 🔗 Sources

* [Simplilearn on Bellman-Ford](https://www.simplilearn.com/tutorials/data-structure-tutorial/bellman-ford-algorithm)
* [Medium Blog](https://medium.com/@maryanngitonga/bellman-fords-algorithm-e2344aa21c7b)
* [YouTube & Google Knowledge](https://www.google.com/search?q=bellman+ford+algorithm)

---

