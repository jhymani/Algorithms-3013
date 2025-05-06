## Exam Questions: Bellman-Ford Algorithm

### Multiple Choice 

1. **What is the primary advantage of the Bellman-Ford algorithm over Dijkstra’s algorithm?**

   A. It is faster for all graphs
   B. It can detect negative weight cycles
   C. It uses less memory
   D. It only works with positive weights
   **→ Answer: B**

3. **What is the time complexity of the Bellman-Ford algorithm for a graph with V vertices and E edges?**
   A. O(V)
   B. O(E + V)
   C. O(VE)
   D. O(E log V)
   **→ Answer: C**

4. **How many times does the Bellman-Ford algorithm relax all the edges in the graph (assuming no early stopping)?**
   A. V - 1
   B. E
   C. V
   D. 2V
   **→ Answer: A**

---

###  Fill in the Blank

1. The Bellman-Ford algorithm is capable of detecting **\_\_\_\_\_\_\_\_\_\_** weight cycles in a graph.
   
   **→ Answer: negative**

3. The process of updating the shortest path estimates in Bellman-Ford is known as **\_\_\_\_\_\_\_\_\_\_**.
   
   **→ Answer: relaxation**

---

##  Bellman-Ford Algorithm Handout 
# Bellman-Ford Algorithm - Student Handout

##  Key Concepts

- Bellman-Ford computes the **shortest path** from a **single source** to all vertices in a weighted graph.
- **Works with negative edge weights**, unlike Dijkstra.
- Can **detect negative weight cycles** in a graph.

---

##  Algorithm Steps

1. **Initialization**  
   - Set all distances to ∞, except the source (0).

2. **Relaxation**  
   - Repeat for V−1 iterations: For every edge (u → v), update dist[v] if `dist[u] + weight < dist[v]`.

3. **Negative Cycle Check**  
   - If any edge can still be relaxed → negative cycle exists.

4. **Output**  
   - Final shortest distances and paths.

---

##  Algorithm Comparison

| Feature              | Bellman-Ford | Dijkstra | Floyd-Warshall |
|----------------------|--------------|----------|----------------|
| Negative Weights     | ✅ Yes       | ❌ No    | ✅ Yes         |
| Detects Neg. Cycles  | ✅ Yes       | ❌ No    | ✅ Yes         |
| Time Complexity      | O(VE)        | O(V²) or O((V+E) log V) | O(V³) |

---

##  Real-World Applications

- **GPS Navigation**: Adjusts routes with changing traffic (supports dynamic weights).
- **Network Routing (e.g., RIP)**: Finds optimal paths, adjusts to failures.
- **Currency Exchange**: Detects arbitrage opportunities via negative cycles.

---


