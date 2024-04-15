## Three Pointers

Why I am talking about three pointers program ? They are very very rarely asked in coding interviews yes
but I would call you are very lucky ! if you see such a problen in your interview, cause I can say there are only 3 questions falling in this category as far as I know.
Let see them one by one.

### Reverse a linklist
Linklist is probably the simplest data structure and it's quite straight forward and simple to solve linkedlist problem with one or two pointes except this one :) 
Because to reverse a linklist you need three pointes yes. Let's see how can we reverse a linklist

Leetcode practice link : https://leetcode.com/problems/reverse-linked-list

1->2->3->null ==>> 3->2->1->null 

* Above example clearly say we need a way to swap
* we need to remember the forward node to swap the current node with the previous node. thats why we need an extra pointer.
* we call these 3 pointers as prev, curr, next(forward)
* prev start from null and at the end return prev <== important

Let's see the this step by step : [Explanation](https://youtu.be/HmZSrU21lrQ)
```
public ListNode reverseList(ListNode head) {
        ListNode prev = null ;
        ListNode curr = head ;

        while(curr != null) {
            ListNode forward = curr.next ; // <== save the next pointer

            curr.next = prev ; // <= swap with prev
            prev = curr ;

            curr = forward ; // <= move to next
        }
        return prev ;
    }
```

### Sort colors ( Dutch flag problem )
This problem is also called Dutch flag problem, where we are asked to sort the members of an array where only 3 numbers are present repeatedly in any order.
e.g _Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue._

Leetcode practice link : https://leetcode.com/problems/sort-colors/

To solve this problem you need three pointers.
* One starting from 0 say start
* Another starting from array end say end
* Another checker which actually scans from start to end and compare and swap the elements to its correct position

This is how you will sort them in place :
```
void swap(int[] nums, int i, int j) {
        int temp = nums[i] ;
        nums[i] = nums[j] ;
        nums[j] = temp ;
    }
    public void sortColors(int[] nums) {
        int start = 0 ;
        int checker = 0 ; //keep tracks of 1
        int end = nums.length - 1 ;
        while(checker <= end) {
            if(nums[checker] == 0) { //checks if number is zero
                swap(nums, start, checker);
                start ++ ;
                checker ++ ;
            }
            else if(nums[checker] == 2) { //checks if number is 2
                swap(nums, checker, end);
                end -- ;
            } else {
                checker ++ ;
            }
        }
    }
```

### Three Sum
This is an extention to 2sum problem where we need to find the triplets for a given target.
e.g _Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.
result wont contain duplicate triplets._

Leetcode practice link : https://leetcode.com/problems/3sum/

To solve this problem you need three pointers.
In short keeping one pointer fixed we can run two pointers logic to find the target duplets. hence we need two forloops and time O(N^2).

* First sort the elements <= very important
* start a pointer starting from 0 to arr.length - 2 we call it k
* Another say i, starting from k + 1 ( which is next pointer )
* Another say j, traversing from end = arr.length - 1
* inner for loop with i and j will find the duplets with target = sum - a[k]
* as the members are sorted hence when a[i] + a[j] < target increment i
* else when a[i] + a[j] > target decrement j
* increment i and decrement j when a duplets is found

This is how you will solve this problem :
```
public List<List<Integer>> threeSum(int[] nums) {
      Arrays.sort(nums) ;

      Set<String> set = new HashSet<>() ;
      List<List<Integer>> result = new ArrayList<>() ;

      for(int k = 0; k <= nums.length - 2 ; k++) {
          int target = 0 - nums[k] ;
          //two sum
          for(int i = k + 1, j = nums.length - 1; i < j;) {
              if(nums[i] + nums[j] == target) {
                  String key = nums[k] + "" + nums[i] + "" + nums[j] ;
                  if(!set.contains(key)) {
                      result.add(Arrays.asList(nums[k], nums[i], nums[j]));
                      set.add(key) ;
                  }
                  i++ ;
                  j-- ;
              }
              else if(nums[i] + nums[j] < target) {
                  i++ ;
              } else {
                  j-- ;
              }
          }
      }
      return result ;
  }
```
