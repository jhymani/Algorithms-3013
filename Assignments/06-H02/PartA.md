Jhymani Joseph

Part A: Conceptual Questions

1. Define Hashing and Collision Resolution

 ### **Hashing:**  
Hashing is a technique that converts data also known as keys into a fixed-size number also known as hash values using a **hash function**. This value determines where the data is stored into the hash table for quick access.  

### **Collision Resolution:**  
A collision happens when two keys generate the same hash value. To handle this, we use:  

a)  What is a hash table and why is collision resolution necessary?

A **hash table** is a data structure that quickly stores and retrieves data using a hash function which assigns keys to specific indexes.  

Collision resolution necessary to prevent data loss. Since each index can technically store only one value, we need a collision resolution method to handle collisions and ensure all data is stored properly.

b) Explain the key differences between open hashing (chaining) and closed hashing (open addressing).

| **Feature**          | **Open Hashing (Chaining)**  | **Closed Hashing (Open Addressing)**  |
|----------------------|----------------------------|------------------------------------|
| **Storage Method**   | Uses linked lists at each index to store multiple keys.  | Stores all keys within the hash table itself.  |
| **Collision Handling** | Colliding elements are stored in a linked list at the same index.  | Colliding elements are placed in the next available slot using probing.  |
| **Memory Usage**     | Uses extra memory for linked lists.  | Uses only the fixed table size, no extra memory.  |
| **Performance**     | Handles collisions efficiently, less affected by clustering.  | Can suffer from clustering, slowing down insertions.  |
| **Best For**        | When many collisions are expected, and dynamic memory is available.  | When memory is limited, and fewer collisions are expected.  |

- **Chaining** keeps multiple values at the same index.  
- **Open Addressing** moves values to the next available spot.  

2. Collision Resolution Techniques

a) Briefly describe at least two methods for resolving collisions in open addressing (e.g., linear probing, quadratic probing, double hashing).

  **Linear Probing** – If a collision occurs, the next available slot is checked sequentially. 
  **Quadratic Probing** – If a collision occurs, instead of moving sequentially, it checks slots in increasing quadratic intervals 

b) Explain the pros and cons of each method.

| **Method**             | **Pros** | **Cons** |
|------------------------|---------|----------|
| **Linear Probing**  | Simple and cache-friendly (good locality). | Causes **primary clustering** (long sequences of occupied slots). |
| **Quadratic Probing** | Reduces clustering compared to linear probing. | Can cause **secondary clustering** and might not find an empty slot if the table isn’t sized properly. |

c) Which collision resolution technique can handle more values than table slots. Explain.

Separate Chaining (Open Hashing) can handle more values than the number of available slots in the hash table.

In separate chaining, each index or bucket in the hash table stores a linked list. This means multiple keys can be stored in the same index, allowing the table to store more values than the number of slots.
The table size only limits the number of linked lists, not the total number of elements that can be stored.

d) What is the worst performance (big oh) for each type of collision resolution technique?

| **Collision Resolution Method** | **Worst-Case Time Complexity (Big-O)** |
|--------------------------------|---------------------------------|
| **Linear Probing**  | **O(n)** (if many collisions cause long probing sequences) |
| **Quadratic Probing**  | **O(n)** (in worst cases, when many probes are needed) |
| **Double Hashing**  | **O(n)** (if the second hash function results in clustering) |


3. Impact of Hash Table Size

a) How does the choice of table size affect the distribution of keys?

- A well-chosen table size helps spread keys evenly, reducing collisions and improving speed.  If the table is **too small**, many keys will compete for the same spots, causing slow lookups. Prime numbers as table sizes generally help avoid patterns that lead to poor distribution.  

b) What are the pitfalls of using a poor table size (for example, a table size that is a round number or a power of 2)?

Powers of 2 can cause patterns where keys **cluster** in certain spots instead of spreading out.  Round Numbers (e.g., 100, 200...) often lead to uneven key distribution, increasing the likelyhood of collisions.  
