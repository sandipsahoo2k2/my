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
     
  3. [Watch this video to find tha path to a node](https://www.youtube.com/watch?v=c1g6leyUuPM)

  4. Vertical Order traversal ( Using map )
     This is an interesting problem frequently asked in coding interviews. [Watch this video](https://youtu.be/x6oAGPNqGzY) and learn howto solve such problems.

  #### Few important questions

  - How to check if a leaf is **Left child** ?
 
    Check if node.left.left is null and node.left.right == null then it's a left child.

  - **maxDepth and minDepth**

	  ```
	  int maxDepth(Tree node)
	  {
		if(node == NULL))
			return 0;
		
		int leftDepth = maxDepth(node.left);
		int rightDepth = maxDepth(node.right);
		//Check max diameter if asked here 
		return 1 + Math.max(leftDepth, rightDepth) ;
	  }
	  ```
   
  	[Practice this minDepth problem from leetcode](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

  	[Watch this solution for minDepth](https://youtu.be/JrrPcXix8zo)

  - **Invert a Tree**
    
    We follow the same DFS approach and write a preOrder traversal code and swap the nodes where we print the root value.
    
    ```
    public TreeNode invertTree(TreeNode root) {
        if(root != null) {
            
            TreeNode temp = root.left ;
            root.left = root.right ;
            root.right = temp ;

            invertTree(root.left) ;
            invertTree(root.right) ;
        }
        return root ;
    }
    ```

  - **Sum Of Distances**
 
    [Practice this Hard problem from leetcode](https://leetcode.com/problems/sum-of-distances-in-tree/)

    [Watch the step by step approach to solve this problem](https://youtu.be/_KAjEdomX7M)

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
    
    It is defined as the node next to the current node in the inorder traversal of tree.

    ```
    inOrderSuccessor(TreeNode node)
    
      if (node.right != null)
          return minTree(node);

      //Look at this code below it's nothing but a linklist traversal and
      //We are telling previous node is successor if curr node is parent
    
      TreeNode curr = node.parent ;
      TreeNode prev = node ;
    
      //Go up the tree from node until we see a node that is the left child of it's parent
      while (curr != null && curr.left != prev) {
          curr = node.parent;
    	  prev = node;
      }
      return curr;
    ```

    There is an interesting problem [leetcode 285] given the root find Inorder Successor in BST
    To solve this problem as there is no parent link in a node, we should use BST property.
    If you closely walk thorough the steps of BST you will realise that if we keep track of a previous node
    only when we go left in a BST then previous node is the successor of the given node.

    ```
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        TreeNode successor = null;
        while (root != null) {
            if (p.val >= root.val) {
                root = root.right;
            } else {
                successor = root; //keep updating when you go left.
                root = root.left;
            }
        }
        return successor;
    }
    ```

  - **Lowest common ancestor**
    
    ```
	public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
	        //base case
	        if (root == null || root == p || root == q) {
	            return root;
	        }
	        TreeNode left = lowestCommonAncestor(root.left, p, q);
	        TreeNode right = lowestCommonAncestor(root.right, p, q);
	
	        //result
	        if(left == null) {
	            return right;
	        }
	        else if(right == null) {
	            return left;
	        }
	        else { //both left and right are not null, we found our result
	            return root;
	        }
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
     
Here is a practice problem from [leetcode medium](https://leetcode.com/problems/top-k-frequent-elements)
      
### How to solve any binary tree problem ?
In my openion, there could only be two types of structure to solve a binary tree problem.
* In One case, we return boolean like [path sum](https://leetcode.com/problems/path-sum/)
* Another we add or subtract find max or min like [max path sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

For any DFS method it is important to come up with the base case e.g if null what will you return, if it’s leaf what will you return. _You must have one case each for when you will return true and a case when you will return false_. Then you call the method recursively for left and right subtree with a Or / And like this.

```
public boolean hasPathSum(TreeNode root, int targetSum) {
        if(root == null) {
            return false ;
        }

        targetSum = targetSum - root.val ; // <-- subtract in each step

        if (root.left == null && root.right == null) {
            return targetSum == 0;
        }

        return hasPathSum(root.left, targetSum) || 
        hasPathSum(root.right, targetSum) ;
    }
```
[Watch this video to know the pattern](https://youtu.be/s2Yyk3qdy3o?si=Wty0P7bZEWyUu2nS)

#### Iterative approach ( For top tier companies )
[Leetcode practice link sum-root-to-leaf-numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers)

This is a very very important problem to practice for any interview. You must solve it iteratively. Recursive solution may look simple but when you are asked to walk through the steps, it is difficult and prone to errors. Hence iterative version.

In this problem we are asked to collect the sum till leaf node, hence we must have a condition to check for a leaf node which is **node.left == null && node.right == null**

Note : Params that you push to stack are the params that goes to your method parameters when you call recursively too.

This is my solution :
```
public int sumNumbers(TreeNode root) {
        Stack<Object[]> st = new Stack<>() ;
        if(root != null) {
            st.push(new Object[]{root, 0}) ;
        }

        int total = 0 ;
        while(!st.isEmpty()) {
            Object[] objects = st.pop() ;
            TreeNode node = (TreeNode) objects[0] ;
            int sum = (int) objects[1] ;

            sum = sum * 10 + node.val ;

            if(node.left == null && node.right == null) {
                total += sum ; //**<-- look here total**
            }

            if(node.right != null) {
                st.push(new Object[]{node.right, sum }) ;
            }

            if(node.left != null) {
                st.push(new Object[]{node.left, sum }) ;
            }
        }

        return total ;
    }
```

## Stanford page
[Refer standford page](http://cslibrary.stanford.edu/110/BinaryTrees.html)
