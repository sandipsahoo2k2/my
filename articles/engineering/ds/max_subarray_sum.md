## 1. Max subarray sum

When we look at this question We tend to think about finding all subarrays for a given array and find the max sum from those list right.
Which is actually a correct answer but when ever there are numbers and some mathematical trick exists. 
So here is a simple intution to this problem if there are only positive numbers, it is so obvious (no one would ask this question). 
Cause in that case sum of all numbers in the entire array is the answer. 
Which means the arrays must have some negative numbers too and if it has some -ve numbers then We use Kadane algorithm.

You may watch this video version of this article [here](https://youtu.be/uJml2MrBCg8)

Its very very simple, in this approach use a running sum and in a forloop

* Any subarray whose sum is positive is worth keeping else throw it away from calculation
* if runningSum is less than zero then reset the runningSum = 0
* update the maxSum if runningSum > maxSum
  
#### Kadane's Approach / a simple math trick :
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

## 2. Subarray Sum Equals K :
Given an array of integers nums and an integer k, return the total number of subarrays whose sum equals to k.

This is a very beautiful question ! Because you not only have to go thorugh each possible subarray but also at the same time you need to make sure the sum is the given sum and finally count how many such subarray exists.

So we definitely have to find the number of all possible subarrays right ?

Let's first write the program to find all possible subarrays for a given array.
**_It's very similar to all possible substring for a given string, So how will we write all substring ?_**

* Use substring() method which is like given two index it returns the substring from location 1st to the last index(excluded).
* Use a simple for loops to find all possible substring

**All Substring :**
- O N^3 -> for substring method
	```
	
	for(int i = 0 ; i < givenString.length() ; i ++) {
		for(int j = i + 1 ; j <= givenString.length() ; j ++) { // Note : <=
			System.out.println(givenString.substring(i, j));
		}
	}
	```
- O N^2 -> not using substring but use i to start the index for j
  
	```
	for(int i = 0 ; i < givenString.length() ; i ++) {
 		String subString = "" ;
		for(int j = i ; j < givenString.length() ; j ++) { // Note : <
 			subString += givenString.charAt(j) ;
			System.out.println(subString);
		}
	}
	```

#### **ID Solution Approach - Acceptable **
  We can simply write the solution with any of the above approach e.g lets take the second approach. O(N^2)
  
  ```
  public int subarraySum(int[] nums, int k) {
        if(nums.length == 0) {
            return 0;
        }
        
	int count = 0 ;
        for(int i = 0; i < nums.length; i ++) {
            int sum = 0;
            for(int j = i; j < nums.length; j ++) {
                sum += nums[j];
                if( sum == k ) {
                    count ++ ;
                }
            }
        }
  	return count ;
    }
  ```
Practice This approach with [Medium Leetcode 560](https://leetcode.com/problems/subarray-sum-equals-k)

#### **ID interview Approach - Gold**

It is worth noting that almost all subarray problems can be solved by keeping track of the runningSum ( with an extra prefiSum in O(N) time sparing an extra O(N) space with a hashMap ).

&#9758; Because if _(A+B+C) + (D+E+F) = targetSum_, then if we see currentSum of (D+E+F) and there exists a _prefixSum = targetSum - (A+B+C)_ then we have a subArray whose sum is targetSum. See the next question uses this intution / hashMap to solve this problem.

**If you are asked :**
* count subArray _init_ the hashMap with a (key, value) = (0, 1) => as there can be a zero sum subarray
* find the subArray then you need the index hence _init_ the hashMap with a (key, value) = (0, -1) => with -1 index

O(N) Approach : [Watch this video](https://www.youtube.com/shorts/x2DxTtx8pEU)
