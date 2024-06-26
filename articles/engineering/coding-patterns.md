## Top 10 coding patterns to solve any coding interview question
Here are the Top 10 patterns that can be used to solve any coding interview question, as well as how to identify each pattern, and some example questions for each. I strongly recommend checking out my videos for those are listed on the home page of this website and practice them before your next interview.

## 1. Sliding Window

The Sliding Window pattern is used to perform a required operation on a specific window size of a given array or linked list, such as finding the longest subarray containing all 1s. Sliding Windows start from the 1st element and keep shifting right by one element and adjust the length of the window according to the problem that you are solving. In some cases, the window size remains constant and in other cases the sizes grows or shrinks.

<img width="400" alt="image" src="https://github.com/sandipsahoo2k2/my/assets/5547869/667acef7-efc8-4283-a5ea-e291879a4b0d">

Following are some ways you can identify that the given problem might require a sliding window:

The problem input is a linear data structure such as a linked list, array, or string
You’re asked to find the longest/shortest substring, subarray, or a desired value
Common problems you use the sliding window pattern with:

Maximum sum subarray of size ‘K’ (easy)  
Longest substring with ‘K’ distinct characters (medium)  
String anagrams (hard)  

Refer : https://interviewdose.com/articles/engineering/ds/sliding_window

## 2. Two Pointers, Fast and Slow pointers

Two Pointers is a pattern where two pointers iterate through the data structure in tandem until one or both of the pointers hit a certain condition.Two Pointers is often useful when searching pairs in a sorted array or linked list; for example, when you have to compare each element of an array to its other elements.

Ways to identify when to use the Two Pointer method:

It will feature problems where you deal with sorted arrays (or Linked Lists) and need to find a set of elements that fulfill certain constraints
The set of elements in the array is a pair, a triplet, or even a subarray
Here are some problems that feature the Two Pointer pattern:

Squaring a sorted array (easy)  
Triplets that sum to zero (medium)  : https://interviewdose.com/articles/engineering/ds/three_pointers
Comparing strings that contain backspaces (medium)  

SuccessSheet:
```
public int fn(ListNode head) {
    ListNode slow = head;
    ListNode fast = head;
    int ans = 0;

    while (fast != null && fast.next != null) {
        // do logic
        slow = slow.next;
        fast = fast.next.next;
    }

    return ans;
}
```

### Fast and Slow pointers
The Fast and Slow pointer approach, also known as the Hare & Tortoise algorithm, is a pointer algorithm that uses two pointers which move through the array (or sequence/linked list) at different speeds. This approach is quite useful when dealing with cyclic linked lists or arrays.

By moving at different speeds (say, in a cyclic linked list), the algorithm proves that the two pointers are bound to meet. The fast pointer should catch the slow pointer once both the pointers are in a cyclic loop.

How do you identify when to use the Fast and Slow pattern?

The problem will deal with a loop in a linked list or array
When you need to know the position of a certain element or the overall length of the linked list.
When should I use it over the Two Pointer method mentioned above?

There are some cases where you shouldn’t use the Two Pointer approach such as in a singly linked list where you can’t move in a backwards direction. An example of when to use the Fast and Slow pattern is when you’re trying to determine if a linked list is a palindrome.
Problems featuring the fast and slow pointers pattern:

Linked List Cycle (easy)
Palindrome Linked List (medium)
Cycle in a Circular Array (hard)

## 3. Merge Intervals

The Merge Intervals pattern is an efficient technique to deal with overlapping intervals. In a lot of problems involving intervals, you either need to find overlapping intervals or merge intervals if they overlap. 

[Learn these exotic techniques to solve such problems](https://interviewdose.com/articles/engineering/ds/meeting_intervals)

## 4. In-place reversal of linked list

In a lot of problems, you may be asked to reverse the links between a set of nodes of a linked list. Often, the constraint is that you need to do this in-place, i.e., using the existing node objects and without using extra memory. This is where the above mentioned pattern is useful.

Refer : https://interviewdose.com/articles/engineering/ds/three_pointers
SuccessSheet :
```
public ListNode fn(ListNode head) {
    ListNode curr = head;
    ListNode prev = null;
    while (curr != null) {
        ListNode nextNode = curr.next; //forward pointer
        curr.next = prev;
        prev = curr;
        curr = nextNode;
    }

    return prev; <== return prev
}
```

How do I identify when to use this pattern:

If you’re asked to reverse a linked list without using extra memory
Problems featuring in-place reversal of linked list pattern:

Reverse a Sub-list (medium)
Reverse every K-element Sub-list (medium)

## 5. Tree BFS

This pattern is based on the Breadth First Search (BFS) technique to traverse a tree and uses a queue to keep track of all the nodes of a level before jumping onto the next level. Any problem involving the traversal of a tree in a level-by-level order can be efficiently solved using this approach.

The Tree BFS pattern works by pushing the root node to the queue and then continually iterating until the queue is empty. For each iteration, we remove the node at the head of the queue and “visit” that node. After removing each node from the queue, we also insert all of its children into the queue.

How to identify the Tree BFS pattern:

If you’re asked to traverse a tree in a level-by-level fashion (or level order traversal)
Problems featuring Tree BFS pattern:

Binary Tree Level Order Traversal (easy)
Zigzag Traversal (medium)

## 6. Tree DFS

Tree DFS is based on the Depth First Search (DFS) technique to traverse a tree.

You can use recursion (or a stack for the iterative approach) to keep track of all the previous (parent) nodes while traversing.

The Tree DFS pattern works by starting at the root of the tree, if the node is not a leaf you need to do three things:

Decide whether to process the current node now (pre-order), or between processing two children (in-order) or after processing both children (post-order).
Make two recursive calls for both the children of the current node to process them.
How to identify the Tree DFS pattern:

If you’re asked to traverse a tree with in-order, preorder, or postorder DFS
If the problem requires searching for something where the node is closer to a leaf
Problems featuring Tree DFS pattern:

Sum of Path Numbers (medium)
All Paths for a Sum (medium)

## 7. Subsets

A huge number of coding interview problems involve dealing with Permutations and Combinations of a given set of elements. The pattern Subsets describes an efficient Breadth First Search (BFS) approach to handle all these problems.

The pattern looks like this:

Given a set of [1, 5, 3]

Start with an empty set: [[]]
Add the first number (1) to all the existing subsets to create new subsets: [[], [1]];
Add the second number (5) to all the existing subsets: [[], [1], [5], [1,5]];
Add the third number (3) to all the existing subsets: [[], [1], [5], [1,5], [3], [1,3], [5,3], [1,5,3]].
Here is a visual representation of the Subsets pattern:

How to identify the Subsets pattern:

Problems where you need to find the combinations or permutations of a given set
Problems featuring Subsets pattern:

Subsets With Duplicates (easy)
String Permutations by changing case (medium)

## 8. Modified binary search

Whenever you are given a sorted array, linked list, or matrix, and are asked to find a certain element, the best algorithm you can use is the Binary Search. This pattern describes an efficient way to handle all problems involving Binary Search.

Refer : https://interviewdose.com/articles/engineering/ds/binary_search

Problems featuring the Modified Binary Search pattern:

Order-agnostic Binary Search (easy)
Search in a Sorted Infinite Array (medium)

## 9. Top K elements

Refer : https://interviewdose.com/articles/engineering/ds/binary_tree

Any problem that asks us to find the top/smallest/frequent ‘K’ elements among a given set falls under this pattern.

The best data structure to keep track of ‘K’ elements is Heap. This pattern will make use of the Heap to solve multiple problems dealing with ‘K’ elements at a time from a set of given elements. The pattern looks like this:

Insert ‘K’ elements into the min-heap or max-heap based on the problem.
Iterate through the remaining numbers and if you find one that is larger than what you have in the heap, then remove that number and insert the larger one.

There is no need for a sorting algorithm because the heap will keep track of the elements for you.

Problems featuring Top ‘K’ Elements pattern:

Top ‘K’ Numbers (easy)
Top ‘K’ Frequent Numbers (medium)
K Pairs with Largest Sums (Hard)

SuccessSheet:
```
public int[] fn(int[] arr, int k) {
    PriorityQueue<Integer> heap = new PriorityQueue<>(CRITERIA);
    for (int num: arr) {
        heap.add(num);
        if (heap.size() > k) {
            heap.remove();
        }
    }

    int[] ans = new int[k];
    for (int i = 0; i < k; i++) {
        ans[i] = heap.remove();
    }
    return ans;
}
```

## 10. Topological sort

Topological Sort is used to find a linear ordering of elements that have dependencies on each other. For example, if event ‘B’ is dependent on event ‘A’, ‘A’ comes before ‘B’ in topological ordering.

Refer : https://interviewdose.com/articles/engineering/ds/topological_sorting

How to identify the Topological Sort pattern:

The problem will deal with graphs that have no directed cycles
If you’re asked to update all objects in a sorted order
If you have a class of objects that follow a particular order
Problems featuring the Topological Sort pattern:

Task scheduling (medium)

https://leetcode.com/explore/interview/card/cheatsheets/720/resources/4723/



