## Topological sort / Course Schedule

Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for 
every directed edge u-v, vertex u comes before v in the ordering. 
Topological Sorting for a graph is not possible if the graph has cycles.

To solve such problem you can use DFS or BFS traversal and see if there is a cycle and
if there is a cycle then you can't have an ordering possible using all the vertex.
But I would say know only one way to solve this e.g BFS in this case why ? 
Because for an interview environment its easy to explain. It's by default linear in nature.

**Below are the steps to solve such problem.**

1. Create a graph(Adgency list) from the input, usually input is a 2d array. Create a graph `List<Integer> gph[] = new ArrayList[size]`
2. Find the inDegrees from the input and add the nodes which has inDegree zero.
3. Perform BFS For each node in the Queue
   poll from the quque <-- add it to the result
   for each child of the nodes neighbours
     decrement inDegree count <-- important
     if( inDegree == 0) -> add it to the queue
4. finally the result contains the vertex in order.

* Leetcode problem to practice i: https://leetcode.com/problems/course-schedule
* Leetcode problem to practice ii: https://leetcode.com/problems/course-schedule-ii



