## Rotate an Array
Let's learn to rotate array first before we dive into the Matrix traversal as they follow same pattern rotate/spiral.

**Take this example :**
_Given an array  of a integers and n number d, perform d left rotations on the array. Return the updated array to be printed as a single line of space-separated integers._ ( [hacker rank](https://www.hackerrank.com/challenges/ctci-array-left-rotation/problem) )

 If d = 2 then [1,2,3,4,5] -> [3,4,5,1,2]

Try to solve it and you will find a pattern, the use of modulo ( % ) .
The solution is to simply do the modulo to find the exact new position for an element in the cell and copy it to a list.

* int newStartPosition = total_rotation % length of array ;
* and Direction when right = use for loop starting from right to left / copy the part of the array from newIndex to end and put it before
* and Direction when left = use for loop starting from left to right / copy the part of the array till newIndex from start and put it before
* **Also note that** every _newIndex = ( a.size() + i + (d * -1) ) % a.size()_;

Similar question with direction to _right_ : https://leetcode.com/problems/rotate-array

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

Check an invalid cell : 
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
