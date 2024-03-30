## Matrix traversal 
What I mean by matrix here is generally a two dimentional matrix. 
There are usually two direction that we can follow to traverse all the cells in a mtrix.
One in the direction of row another with column, greedily traverse in each direction until you must stop, then turn around and head in the other direction.
So while solving such problems make sure that you come up with the right direction array for row and column.

**Let's take an example :**
Given an m x n matrix, return all elements of the matrix in spiral order.

Leetcode question reference : [https://leetcode.com/problems/spiral-matrix](https://leetcode.com/problems/spiral-matrix)

Spiral order hence :
* rowDirection = [east, south, west, north] -> [0, 1, 0, -1]
* colDirection = [east, south, west, north] -> [1, 0, -1, 0]

For every such problem : 
* Create a method to check an invalid cell

For every such problem : 
* We must use a visited set to track the visisted cells

Handle an invalid move :
* We have to do use a modulo % on the direction to start when we hit the boundary
* Whenever there is a spiral thingy it's common :)

Here is our solutiuon :
```
boolean isInvalid(int row, int col, int[][]matrix) {
        if(row < 0 || col < 0 || row >= matrix.length || col >= matrix[row].length || matrix[row][col] == 1000) {
            return true ;
        }
        return false ;
    }

    public List<Integer> spiralOrder(int[][] matrix) {

        List<Integer> result = new ArrayList<>() ;
        int rowDir[] = new int[]{0, 1, 0, -1};
        int colDir[] = new int[]{1, 0, -1, 0};

        int totalNumbers = matrix.length * matrix[0].length ;
        int count = 0, row = 0, col = 0 ;
        int dirIndex = 0 ; // start from 0 so +1 to mod

        while(count++ < totalNumbers) {
            result.add(matrix[row][col]) ;
            matrix[row][col] = 1000 ; //set visited
            row = row + rowDir[dirIndex] ;
            col = col + colDir[dirIndex] ;
            if(isInvalid(row, col, matrix)) {
                //bring inside boundary
                row = row - rowDir[dirIndex] ;
                col = col - colDir[dirIndex] ;
                //fix the direction
                dirIndex = (dirIndex + 1) % 4 ;
                //move the cell for the wrong move
                row = row + rowDir[dirIndex] ;
                col = col + colDir[dirIndex] ;
            }
        }
        return result ;
    }
```
[Video reference](https://youtu.be/J8TkpdvbRcE)
