## Trees Examples and Codes

* A **Binary Tree** is made of nodes, where each node contains a left pointer, a right pointer, and a data element.
It is either empty (represented by a null pointer), or is made of a single node of which
the left and right pointers each point to a binary tree.

* A **Binary Search Tree (BST)** or ordered binary tree is a type of binary tree where the _nodes are arranged
in order_: for each node, all elements in its left subtree are less-or-equal to the node (<=), 
and all the elements in its right subtree are greater than the node (>).

* The last tree out of major kinds of trees is a **Heap**. _A heap is a tree in which each node's children have values
less than or equal to node's value_. Consequently, the root node always has the largest value in the tree, 
which means that it's possible to find the maximum value in constant time: Simply return the root value. 
So, if extraction the max / min value needs to be fast, we should use a heap.
