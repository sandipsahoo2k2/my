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

### Checking if two intervals overlap
Be familiar with writing code to check if two intervals overlap.

```java
boolean isOverlap(int[]first, int[]second):
  return first[0] < second[1] and second[0] < first[1]
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

### High Probability Questions
Merge Interval - Use Array Sort : https://leetcode.com/problems/merge-intervals/ (vimp) 

Intersection interval - Use PQ Sort : https://leetcode.com/problems/interval-list-intersections/

Watch this meeting rooms problem : https://youtu.be/vjMMBIfvXxI

&#9758; Never forget to set the prev interval to curr in the while loop :)

Meeting rooms - Use PQ Sort - https://leetcode.com/problems/meeting-rooms

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

Meeting rooms ii - Use Array sort with PQ Sort - https://leetcode.com/problems/meeting-rooms-ii/


