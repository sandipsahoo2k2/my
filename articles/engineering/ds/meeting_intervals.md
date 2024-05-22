## Meeting Intervals

Tricks to solve such problems are
1) Sort by first index - Some times use &#9758; Priority Queue to do further sorting on second index
3) Intersect blindly and compare if the result is a valid interval e.g a[0] <= a[1] if it's not merge interval
4) For traversing always check with end value not first value e.g a[1] < b[1] then i++

&#9758; One special case, When you [merge intervals](https://leetcode.com/problems/merge-intervals) - use array sort then merge by reference with prev and add curr interval to result.
   
```java
  if(first[1] < second[1]) {
      i++ ;
  } else {
      j ++ ;
  }
```

A common routine for interval questions is to **sort the array of intervals by each interval's starting value**. This step is crucial to solving the Merge Intervals question.

```java
  Array.sort(intervals, (a, b) -> (a[0] - b[0]) ;
```

[Watch this easy meeting rooms problem](https://youtu.be/vjMMBIfvXxI)
### Checking if two intervals overlap
Be familiar with writing code to check if two intervals overlap.

```java
boolean isOverlap(int[]first, int[]second):
  return first[0] < second[1] && second[0] < first[1]
```

Trick to remember: both the higher pos must be greater then ( or equal to ) both lower pos.

Intersection two intervals
```java
int[] intersection(int[]first, int[]second):
  return new int[]{Math.max(first[0], second[0]), Math.min(first[1], second[1])} ;
```

Merging two intervals ( just opposit careful )
```java
int[] mergeInterval(int[]first, int[]second):
  return new int[]{Math.min(first[0], second[0]), Math.max(first[1], second[1])} ;
```

### Simpler way to check interval overlap

&#9758; Blindly intersect the two intervals by intersection() then check if result is a valid interval 
e.g a[0] <= b[1] start is less than end

```java
int[] overlap = intersection(first, second) ; //find intersection
  if(overlap[0] <= overlap[1]) { <== look how simple just check if valid interval
    result.add(overlap) ;
  }
```

[Learn how interval intersection problems are solved](https://youtu.be/mN7YcWj08-M)
### High Probability Questions
Merge Interval - Use Array Sort, work on reference and prev pointers : https://leetcode.com/problems/merge-intervals (vimp) 

Intersection interval - Blind intersect and traverse the entire array : https://leetcode.com/problems/interval-list-intersections

&#9758; Never forget to set the prev interval to curr in the while loop :)

Meeting rooms - detect a overlap and return - https://leetcode.com/problems/meeting-rooms

```java
  int[] prev = pq.poll() ;
  while(!pq.isEmpty()) {
      int[] curr = pq.poll() ;
      if(curr[0] < prev[1]) {
          return false ;
      }
      prev = curr ; // very very important
  }
```

Meeting rooms ii - Use Array sort and PriorityQ Sort with endTime - https://leetcode.com/problems/meeting-rooms-ii

* How to explain this problem is important
  >There are two scenarios possible here for any meeting. Either there is no meeting room available and a new one has to be allocated,
  or a meeting room has freed up and this meeting can take place there.
  >
  > we can make use of a min-heap to store the end times of the meetings in various rooms.
  So, every time we want to check if any room is free or not, simply check the topmost element of the min heap as that would be the
  room that would get free the earliest out of all the other rooms currently occupied.

If the room we extracted from the top of the min heap isn't free, then no other room is. So, we can save time here and simply allocate a new room.

[Meeting rooms ii Solution](https://youtu.be/Mfd3EDnJejY)

#### Generic Overlap Method
Take a look at a better **Generic Overlap** method that should be used for all such problems

```
int[] overlap(int[] prev, int[] curr){ //[1,4],[2,3]
        int start = Math.max(prev[0], curr[0]); //2
        int end = Math.min(prev[1], curr[1]); //3

        int startMin = Math.min(prev[0], curr[0]); //1
        int endMax = Math.max(prev[1], curr[1]); //4
        return new int[]{start, end, startMin, endMax} ;
    }
```
* Look at this method return, test with [1,2][3,4] -> will return [start, end] = [3,2] which is _an invalid entry_ which can be tested by `if(start <= end)` ( as not valid ), which tells that they don't intersect .
  
* Now test with [1,4],[3,5] -> will return [start, end] = [3,4] which is valid which means they intersect and if you want to merge them you can use [startMin, endMax] for your answer which is [1,5] .
* Now test with [1,4],[2,3] -> will return [start, end] = [2,3] which is valid means they intersect and if you want to merge them you can use [startMin, endMax] for your answer which is [1,4] .
