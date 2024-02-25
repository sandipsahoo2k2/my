## Binary Trees Examples and Techniques

![image](https://github.com/sandipsahoo2k2/my/assets/5547869/82d56a1d-c180-4b6a-998f-7330ba0b6968)

* A **Binary Tree** is made of nodes, where each node contains a left pointer, a right pointer, and a data element.
It is either empty (represented by a null pointer), or is made of a single node of which
the left and right pointers each point to a binary tree.
  #### Tree traversal techniques
  
  1. **DFS** - Depth First Search ( recursion / Stack )
     
    * Pre-order - Recursively Search _root node before_ left and right subtrees - F B A D C E G I H

      _This recursive technique is used to solve most of the tree problems_ [Watch this example](https://youtu.be/0EjPBPRLyjE)
      ```
      void preOrder(Node node) {
        if (node != null){
          print(node.key); // Check the root first
          preOrder(node.left);
          preOrder(node.right);
        }
      ```
    * In-order - Recursively Search left then _root node in middle_ and then right subtrees
      ```
      void inOrder(Node node) {
        if (node != null){
          inOrder(node.left);
          print(node.key); //Check root in the middle
          inOrder(node.right);
        }
      ```
      **A B C D E F G H I**

      &#128073; When you reverse the order for the inOrder [right node, root, left node] it is reverseOrder traversal
    * Post-order - Recursively Search _root node after_ left and right subtrees - A C E D B H I G F
      
  2. **BFS** - Breadth Frist Search  ( Queue )
     
    * Use a Queue to search the nodes instead of stack.
      
      It is also called [level order traversal](https://youtu.be/0C8nLoIQvfA)
      
      &#128073; Remember to use always **_two loops_** while using BFS.
      - A while loop checking on the queue.isEmpty()
      - another for loop on the size of the queue on each iteration which tells the size of that level

  3. Vertical Order traversal ( Using map )
     This is an interesting problem frequently asked in coding interviews. [Watch this video](https://youtu.be/x6oAGPNqGzY) and learn how to solve such problems.

  #### Few important operations

  **maxDepth and minDepth**

  ```
  int maxDepth(Tree node)
  {
	if(node == NULL))
		return 0;
	
	int leftDepth = maxDepth(node.left);
	int rightDepth = maxDepth(node.right);
	
	return 1 + Math.max(leftDepth, rightDepth) ;
  }
  ```

  [Practice this minDepth problem from leetcode](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

  [Watch this solution for minDepth](https://youtu.be/JrrPcXix8zo)


* A **Binary Search Tree (BST)** or ordered binary tree is a type of binary tree where the _nodes are arranged
in order_: for each node, all elements in its left subtree are less-or-equal to the node (<=), 
and all the elements in its right subtree are greater than the node (>).

  - One interesting problem is [here] (https://leetcode.com/problems/validate-binary-search-tree/) where students struggle to prove a binary tree is a BST.
    
    When you do an **inOrder** traversal on a BST it returns members in **increasing order**. After that we can traverse the list      and if  each next element is greater than the previous element, we can say that the tree is BST. This is one simpler way to        validate but we can do better than that in one pass by following the below approach. 
    
    ```
    public boolean isValidBST(TreeNode root) {
        return helper(root, Long.MIN_VALUE, Long.MAX_VALUE) ;
    }
    boolean helper(TreeNode root, long lBound , long hBound) {
        if(root == null) {
            return true ;
        }
        if(root.val <= lBound || root.val >= hBound) {
            return false ;
        }
        return helper(root.left, lBound, root.val) && helper(root.right, root.val, hBound) ;
    }
    ```

    
  - **Deleting a key** from a binary search ( deleteKey())
    
    This is a little bit tricky. We can categorize it in three groups depending on it's operations:
    
      1. A leaf node -> this is the easiest case and we just delete it.
      2. A node that has only one child -> The child replaces the parent.
      3. A node that has both left and right child ->
         We replace the node with **it's predecessor**.


  - **In-Order Successor**

  
    ```
    inOrderSuccessor(TreeNode node)
      if (node.right != null)
          return minTree(node);
    
      TreeNode parent = node.parent ;
      //go up the tree from node until we see a node that is the left child of it's parent
      while (node != null && node == parent.right) {
          node = parent;
          parent = node.parent;
      }
      return parent;
    ```

  - ** Lowest common ancestor **
    
    ```
	TreeNode lowestCommonAncestor(TreeNode node, TreeNode p, TreeNode q) 
	{
		if(node == null)
    			return null;
    
		if(node->left == p || node->left == q || node->right == p || node->right == q)
    			return node;
	
		TreeNode left = lowestCommonAncestor(node->left,p,q);
		TreeNode right = lowestCommonAncestor(node->right, p,q);
		if(left != null && right != null) 
			return node;
		else 
			return (left != null) ? left : right;
	}
    ```
        
#### Max Heap
A **Max heap** is a tree in which each node's children have values less than or equal to node's value.
Consequently, the root node always has the largest value in the tree, which means that it's possible to find
the maximum value in constant time: Simply return the root value.

  Like wise there is **Min Heap** whose node's children values greater than its node's value. So, if extraction the min value needs to be fast, we should use a min heap.
  
  Questions solved using heaps are very very easy and there are very few kinds too. Hence listing everything that you need to know for your next interview in few lines below.
  
  * Time complexity for Building a Binary Heap is O(n) - ( Why ? ) 
  * **Java** has a class called `**PriorityQueue**` which by _default_ creates a **Min Heap**
  * To create a **Max Heap** you can pass the reverse comparator in constructor
    ```
      PriorityQueue<Integer> pQueue
            = new PriorityQueue<Integer>(
                Collections.reverseOrder());
    ```
    * Most of the questions involve a fixed size heap.
      So use constructor with size for such problems e.g `new PriorityQueue(int size)`
    * While solving a problem using heap you will mostly use _only three methods_

      1. add / offer ( < element> ) -> Inserts the specified element -> log(n) time complexity

      2. poll() -> Retrieves and removes the head of this queue -> O(1) time complexity

      3. peek() -> Retrieves, but does not remove, the head of this queue -> O(1) time complexity
      
