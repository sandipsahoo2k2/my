## Sliding window

1. initialise a left pointer starting with zero index
2. write a for loop taking right index
   1. inside the loop add the arr[right] to the window  
   2. Create a condition for the while loop to shrink left [ if required ]
   3. run the while loop on the condition [ which will shrink the window with left pointer
   4. remove the arr[left] from window
   5. increase left ++
3. Update the answer or Do max / min = ( right - left + 1) 

Here's the pseudocode for a general template:

```
public int slidingWindow(int[] arr) {
    int left = 0, ans = 0, curr = 0;

    for (int right = 0; right < arr.length; right++) {

        // Do some logic to "add" element at arr[right] to window
        // or create a conditoon for the below loop to shirnk the window left

        while (WINDOW_CONDITION_BROKEN) { //make sure you are not working on right index in this loop

            // Do some logic to "remove" element at arr[left] from window
            left++;
        }

        //Do some logic like below to update the answer
        //Do max / min size = ( right - left + 1) 
    }

    return ans;
}
```

Try to write the code follow the exact steps given here and solve this first.  
Practice link : https://leetcode.com/problems/max-consecutive-ones/  
Note : Use condition for the while loop  `while(zeroCount == 1)`

```
public int longestOnes(int[] nums) {
        int left = 0 ;
        int zeroCount  = 0 ;
        int maxCount = 0 ;
        for(int right = 0 ; right < nums.length; right ++) {

            if(nums[right] == 0) {
                zeroCount ++ ;
            }

            //we are bringing left pointer to zero when we see a zero.
            while(zeroCount == 1) { <== look at this
                if(nums[left] == 0) {
                    zeroCount -- ;
                }
                left ++ ;
            }

            maxCount = Math.max(maxCount, right - left + 1) ;

        }
        return maxCount  ;
    }

```

Now try this problem : https://leetcode.com/problems/max-consecutive-ones-iii  
By Changing the condition of while loop to `while(zeroCount == k + 1)`

Watch these videos for indepth explanations and more problems:
1. https://youtu.be/HGnHfU3cHc8
2. https://youtu.be/CynfIgY6Aek
