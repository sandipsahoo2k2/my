## Merge Intervals

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
