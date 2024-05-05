<!-- Draft -->
## Graph traversal approach ( DFS and BFS )
BFS is better suited than DFS. 
In DFS, we would have to keep track of and compare the path lengths in case a node (l,r) is visited for a second time,
and terminate the traversal if the current path length is greater than the previous one. 
Otherwise, update the path length to that node and keep exploring.
Hence DFS would be inefficient and also harder to implement.
