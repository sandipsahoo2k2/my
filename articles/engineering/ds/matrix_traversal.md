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
* **Also note that** every _newIndex = ( a.size() + index + (total_rotation * direction) ) % a.size()_;

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
* We must use a visited set to track the visited cells

Handle an invalid move :
* We have to do use a modulo % on the direction to start when we hit the boundary
* Whenever there is a spiral thingy it's common :)

Here is our solutiuon :
```
boolean isValid(int row, int col, int[][]matrix) {
        if(row < 0 || col < 0 || row >= matrix.length || col >= matrix[row].length) {
            return false ;
        }
        if(matrix[row][col] == Integer.MIN_VALUE) {
           return false ;
        }
        return true ;
    }

    public List<Integer> spiralOrder(int[][] matrix) {

        List<Integer> result = new ArrayList<>() ;
        int direction[][] = new int[][]{{0,1},{1,0},{0,-1},{-1,0}};

        int totalNumbers = matrix.length * matrix[0].length ;
        int count = 0, row = 0, col = 0 ;
        int dirIndex = 0 ;// start from 0 so +1 to mod

        while(count++ < totalNumbers) {
            result.add(matrix[row][col]) ;
            matrix[row][col] = Integer.MIN_VALUE ;

            row = row + direction[dirIndex][0] ;
            col = col + direction[dirIndex][1] ;
            if(!isValid(row, col, matrix)) {
                //bring inside boundary
                row = row - direction[dirIndex][0] ;
                col = col - direction[dirIndex][1] ;
                //fix the direction
                dirIndex = (dirIndex + 1) % 4 ;
                //move the cell for the wrong move
                row = row + direction[dirIndex][0] ;
                col = col + direction[dirIndex][1] ;
            }
        }
        return result ;
    }
```
[Video reference](https://youtu.be/J8TkpdvbRcE)

## Diagonal Traverse

```
Input: mat = [1,2,3]
             [4,5,6]
             [7,8,9]]
Output: [1,2,4,7,5,3,6,8,9]
```

[Practice link](https://leetcode.com/problems/diagonal-traverse)

If you look at this problem you will see that they move diagonally. 1st up and then down and then up again and continue this zig zag run.
We can solve this problem using a simple approach traversing the matrix always in one direction and copying and reversing the elements when we go up isn't it. To further optmise it, we can **_use an ArrayDeque_** and we don't need to reverse it.

This is my solution :
```java
public ArrayDeque<Integer> collect(int[][] mat, int i, int j, boolean up) {

        ArrayDeque<Integer> adq = new ArrayDeque<>() ;
        while(isValid(mat,i ,j)){
            if(up) {
                adq.addFirst(mat[i][j]);
            } else {
                adq.addLast(mat[i][j]);
            }
            mat[i][j] = Integer.MIN_VALUE ;
            i ++ ;
            j -- ;
        }
        return adq ;
    }

    public int[] findDiagonalOrder(int[][] mat) {
        List<Integer> result = new ArrayList<>();
        boolean up = true ;
        for(int i = 0 ; i < mat.length ; i++) {
            for(int j = 0 ; j < mat[i].length ; j++) {
                if(mat[i][j] != Integer.MIN_VALUE) {
                    ArrayDeque<Integer> temp = collect(mat, i , j, up) ;
                    result.addAll(temp) ;
                    up = !up ;
                }
            }
        }
        return result.stream().mapToInt(i -> i).toArray() ;
    }
```
