## Graph Traversal

For Graph traversals, we can follow either DFS or BFS approach.

Many of the matrix traversal questions fall under graph traversal category.
Matrix traversals are nothing but graph traversal. The reason is simple each element can be treated as vertex and all of it's neighbours are cells sitting to it's 4 directions.

- When ever question asks about finding a max use DFS
- When ever question asks about finding a min use BFS ( using queue -> find total number of levels to reach the node )


[Find minm no of flips required to connect the two islands](https://leetcode.com/problems/shortest-bridge)

```java
class Solution {

    int[][] getDirections(){
        return new int[][]{{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
    }

    boolean isValid(int i, int j, int[][] grid) {
        if(i < 0 || j < 0 || i >= grid.length || j >= grid[i].length) {
            return false ;
        }
        return true ;
    }

    void dfs(int[][] grid, int i, int j, Queue<int[]> dq){
        if(!isValid(i,j, grid)) {
            return ;
        }
        if(grid[i][j] != 1){ <<-- LOOK this
            return ;
        }

        grid[i][j] = -1 ; //visited
        dq.add(new int[]{i, j});

        for(int[] pair : getDirections()){
            dfs(grid, i + pair[0], j + pair[1], dq);
        }
    }

    public int shortestBridge(int[][] grid) {
        Queue<int[]> dq = new ArrayDeque<>() ;
        boolean found = false ;
        for(int i = 0 ;!found && i < grid.length ; i ++) {
            for(int j = 0 ; j < grid[i].length ; j++) {
                if(grid[i][j] == 1) {
                    dfs(grid, i, j, dq) ;
                    found = true ;
                    break ;
                }
            }
        }

        int step = 0 ;
        while(!dq.isEmpty()) {
            int size = dq.size() ;
            for(int i = 0 ; i < size ; i++) {
                int[] node = dq.poll() ;
                for(int[] pair : getDirections()){
                    int x = node[0] + pair[0] ;
                    int y = node[1] + pair[1] ;
                    if(!isValid(x,y, grid)){
                        continue ;
                    }

                    if(grid[x][y] == 1) { //reached the 2nd iLand
                        return step ;
                    }

                    //as 0 are the path we are taking to reach to 2nd iland
                    //check only zero as here <- be careful
                    if (grid[x][y] == 0) {  // if not seen add to queue
                        dq.offer(new int[]{x, y});
                        grid[x][y] = -1; //set visited
                    }
                }
            }
            ++ step ;
        }
        return step ;
    }
}
```
