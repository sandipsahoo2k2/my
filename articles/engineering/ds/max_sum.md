## Max subarray sum

When we look at this question We tend to think about finding all subarrays for a given array and find the max sum from those list right.
Which is actually a correct answer but when ever there are numbers and some math operation there is always a trick. 
So here is a simple intution to this problem if there are only positive numbers no one would ask this question. 
Cause in that case sum of all numbers in the entire array is the answer. 
Which means the arrays must have some negative answers too and if it has some -ve numbers then We use Kadane algorithm.

Its very very simple, in this approach use a running sum and

* if running sum is less than zero then maxSum = 0
* update the maxSum if currentSum > maxSum
  

#### Plain vanilla approach :
```
	int sum = 0 ;
  int maxSum = Integer.MIN_VALUE ;
  for(int i = 0 ; i < nums.length ; i++) {
      sum += nums[i] ;
      if(sum > maxSum) {
          maxSum = sum ;
      }
      if(sum < 0) {
          sum = 0 ;
      }
  }
```

Practice This approach with [Medium Leetcode 53](https://leetcode.com/problems/maximum-subarray)

#### Subarray Sum Equals K :
Given an array of integers nums and an integer k, return the total number of subarrays whose sum equals to k.
[Video 1](https://www.youtube.com/watch?v=I6viYY0mS6I&start=52s)
