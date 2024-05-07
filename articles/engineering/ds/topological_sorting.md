## Topological sort / Course Schedule

Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for 
every directed edge u-v, vertex u comes before v in the ordering. 
Topological Sorting for a graph is not possible if the graph has cycles.

To solve such problem you can use DFS or BFS traversal and see if there is a cycle and
if there is a cycle then you can't have an ordering possible using all the vertex.
But I would say know only one way to solve this e.g BFS in this case why ? 
Because for an interview environment its easy to explain. It's by default linear in nature.

**Below are the steps to solve such problem.**

1. Create a graph(Adgecency list) from the input, usually input is a 2d array. Create a graph `List<Integer> gph[] = new ArrayList[size]`
2. Find the inDegrees from the input and add the nodes to Queue which has inDegree zero.
3. Perform BFS For each node until Queue is not empty 
      > poll from the quque <-- add it to the result  
      > for each child of the nodes neighbours  
      >> decrement inDegree count <-- important  
      >> if( inDegree == 0) -> add it to the queue
4. finally the result contains the vertex in order.

T: O(V + E) where V = number of vertices and E is number of edges  
S: O(V + E)

For a prerequisites[][] which has n directed edges e[1] -> e[0], this is how you would create a graph.

```java
    int[] inDegrees = new int[numOfTasks] ;
     for(int[] edge : tasks){
         inDegrees[edge[0]] ++ ;
         graph[edge[1]].add(edge[0]) ;
     }
```
Practice questions :
* Learn step by step : https://youtu.be/N4jQQPg1tvA
* [Check if it is possible to finish all courses](https://leetcode.com/problems/course-schedule)
* [return the topological ordering](https://leetcode.com/problems/course-schedule-ii)



