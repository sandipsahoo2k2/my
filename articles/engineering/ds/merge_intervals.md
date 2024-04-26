## Merge Intervals

Tricks to solve such problems are
1) sort by first index - most of the times use priority Queue to do this
2) merge blindly and compare if the result is a valid interval e.g a[0] <= b[0]
3) For traversing always check with end value not first value e.g a[1] < b[1] then i++
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

Merging two intervals
```java
int[] mergeInterval(int[]first, int[]second):
  return new int[]{Math.max(first[0], second[0]), Math.min(first[1], second[1])} ;
```

### Simpler way to check interval overlap

Blindly merge the two intervals by mergeInterval() then check if result is a valid interval 
e.g a[0] <= b[0]

```java
int[] overlap = mergeInterval(first, second) ;
  if(overlap[0] <= overlap[1]) { <== look how simple just check if valid interval
    result.add(overlap) ;
  }
```

Leetcode practice 1 : https://leetcode.com/problems/interval-list-intersections/
Leetcode practice 2 : https://leetcode.com/problems/interval-list-intersections/
Watch this : https://leetcode.com/problems/meeting-rooms

