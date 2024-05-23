## Deep Copy

A deep copy of an object is a copy whose properties do not share the same references (point to the same underlying values) as those of the source object from which the copy was made. 
As a result, when you change either the source or the copy, you can be assured you're not causing the other object to change too.

As the definition says we need to make sure that the exact copy with value it holds and completely new reference is mantra.
* In an interview you might get asked to create deep copy for a list or tree or graph. Solve these problems from leetcode
  
  1. https://leetcode.com/problems/copy-list-with-random-pointer
  2. https://leetcode.com/problems/clone-graph/
 
Trick to solve these problems is to traverse the data structure and push the nodes to a HashMap<CurrentNode, ClonedNode> with key = CurrentNode and Value as ClonedNode.
and Finally return the reference from HashMap for the given node.

