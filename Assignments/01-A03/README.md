A binary tree is a hierarchical and systematic data structure in C++ where each node can have at most two children. 

A node is a basic building block of a binary tree. It has data within it's pointers, which points to itself with left and right children. The topmost node in the tree is known as a root, and a node that has no children is known as a leaf.

According to geeksforgeeks.com "A Binary Search Tree is a data structure used for organizing and storing data in a sorted manner. Binary search tree follows all properties of binary tree and for every nodes, its left subtree contains values less than the node and the right subtree contains values greater than the node."

 ![1_8_QJ6hYqWdLomvwNt6ydBg](https://github.com/user-attachments/assets/bc054bcb-ad05-4c03-acc0-758fe89a49f5)

# Functions Possible In Binary Search Trees:

1. Insertion: This adds a new value to the tree while maintaining the binary search property.
How it works: It starts from the root. If the new value is smaller than the current node's value, move to the left child; if larger, move to the right. Repeat until you find an empty spot to insert the value.

2. Search: This locates a value that exists in the tree.
How it works: It starts from the root and compares the value with the current node. If it's smaller, move to the left; if larger, go right. Continue until you find the value or reach nullptr (not found).

3. Traversal: This visits all nodes in a specific order.
Types:

In-order: Left subtree → Node → Right subtree (gives sorted order for a BST).

Pre-order: Node → Left subtree → Right subtree.

Post-order: Left subtree → Right subtree → Node.

4. Find Minimum/Maximum: This finds the smallest or largest value in the tree.

How it works:
Find minimum: Keep moving to the left child until you reach a node with no left child.

Find maximum: Keep moving to the right child until you reach a node with no right child.

5. Height/Depth Calculation: This determines how tall the tree is (the number of levels).
How it works: Recursively calculate the height of the left and right subtrees and return the larger value plus one.

6. Check if BST is Balanced: To check if the tree is balanced (the height difference between the left and right subtrees is not more than 1 for all nodes).
How it works: Recursively checks the height of the left and right subtrees and compares their difference.

7. Successor/Predecessor: To find the next higher or lower value relative to a given node.

Successor: The smallest value larger than the current node, typically the leftmost node in the right subtree.

Predecessor: The largest value smaller than the current node, typically the rightmost node in the left subtree.

e.g. ![Inorder-Predecessor-and-Successor-in-Binary-Search-Tree](https://github.com/user-attachments/assets/68cc5ffe-41ac-47bf-8470-36af5713f9be)
 
The predecessor of node 25 is the rightmost element in the left of the subtree, which is 20. The successor of node 25 is the leftmost element in the right of the subtree, which is 35.

8. Deletion: This removes a value from the tree while keeping the general structure  of it intact.

There are three cases:

Leaf node (no children): Just remove the node.

One child: Replace the node with its child.

Two children: Replace the node with its in-order successor (the smallest node in the right subtree) and delete the successor.

According to Chatgpt:

# **Node with No Children (Leaf Node)**

- The node is a leaf, meaning it has no left or right children.
- How to delete: Simply remove the node from the tree.

   **Example**:
   ```
         10
        /  \
       5    15
           /
          12
   ```
   If we delete `12`, we just remove it, and the tree becomes:
   ```
         10
        /  \
       5    15
   ```

# **Node with One Child**

- The node has **only one child** (either left or right).
- How to delete: Replace the node with its child. This keeps the BST property intact, as the child will still maintain the correct order.

   **Example**:
   ```
         10
        /  \
       5    15
            /
           12
   ```
   If we delete `15`, we replace it with its left child (`12`):
   ```
         10
        /  \
       5    12
   ```

# **Node with Two Children**

- The node has **two children** (left and right).
- How to delete: This is the most complex case. we need to replace the node with a value that preserves the general BST structure. There are two common ways to do this:

   - Replace with its in-order predecessor: The largest value in the left subtree (the rightmost node of the left subtree).
   - Replace with its in-order successor: The smallest value in the right subtree (the leftmost node of the right subtree).

   Once we have chosen the replacement value, we swap the values and then delete the node in the subtree where the replacement came from. Which will either be just a leaf or it may have just have one child.

   **Example**:
   ```
         20
        /  \
       10   30
      /  \    \
     5   15   40
   ```
   If we delete `20`:
   - Find the in-order successor (smallest value in the right subtree): `30`
   - Replace `20` with `30`, and then delete `30` from the right subtree.

   The tree becomes:
   ```
         30
        /  \
       10   40
      /  \
     5   15
   ```

Code Example for Deletion from geeksforgeeks.org:

```
struct Node {
    int value;
    Node* left;
    Node* right;
    Node(int val) : value(val), left(nullptr), right(nullptr) {}
};

// Find the minimum value node in the right subtree
Node* findMin(Node* root) {
    while (root->left != nullptr)
        root = root->left;
    return root;
}

// Delete a node in the BST
Node* deleteNode(Node* root, int key) {
    if (!root) return nullptr;  // Base case: empty tree

    if (key < root->value) 
        root->left = deleteNode(root->left, key);  // Go left
    else if (key > root->value) 
        root->right = deleteNode(root->right, key);  // Go right
    else {
        // Node to be deleted found
        if (!root->left) {  // Case 1 and 2: One or no child
            Node* temp = root->right;
            delete root;
            return temp;
        }
        else if (!root->right) {
            Node* temp = root->left;
            delete root;
            return temp;
        }

        // Case 3: Two children
        Node* temp = findMin(root->right);  // Find successor
        root->value = temp->value;  // Replace value
        root->right = deleteNode(root->right, temp->value);  // Delete successor
    }
    return root;
}
