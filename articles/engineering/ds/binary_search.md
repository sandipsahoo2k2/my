## Binary search

Binary Search is a **searching algorithm** for finding an element's position in a **sorted array**.

In this approach, the element is always searched in the middle of the given array.

<u>Example:</u>

Consider an array[] = [2, 5, 8, 12, 16, 23, 38] 
* if target = 23
We need to return the position = 5

* if target = 40
We need to return the position = -1

<u>Solution Approach :</u> 
*Run a loop or test recursively*

* mid = start + (end - start) / 2
* if array[mid] == target ??

#### Recursive plain vanilla approach :
```
	int bSearch(int[] array, int start, int end, int target) {
		if(start > end || array.length == 0) {
			return -1 ;
		}
	
		int mid = start + (end - start) / 2 ;
		if(array[mid] == target) {
			return mid ;
		}
	
		if(array[mid] < target) {
			return bSearch(array, start + 1, end, target) ;
		} else {
			return bSearch(array, start, end - 1, target) ;
		}
	}
```

Practice This approach with [Easy Leetcode 704](https://leetcode.com/problems/binary-search/)

#### &#128073; ID approach (Exotic -> Interviewdose ) :
Watch in detailed about this approach in this [Video 1](https://www.youtube.com/watch?v=I6viYY0mS6I&start=52s)

```
	int exoticBSearch(int arr[], int target) {
		int start = 0;
		int end = nums.length ;
		while( start < end) {
			int mid = start + (end - start) / 2 ;
			if( nums[mid] < target) { // <== less or greater here
					start = mid + 1 ;
			} else  { //make sure equals to condition stays here
					end = mid ;
			}
		}
			
		//return start ; /* this will return the insertion point for a non existing element */
		
		return start ==  nums.length ? -1 : nums[start] == target ? start : -1 ;
	}
```

Using the same exotic search we can find the minm index in a rotated array 
&#128073; condition here is if nums[mid] > nums[end) check if the mid value is greater than greatest element
```java
	int end = nums.length - 1; // <==== See this end
	while(start < end) {
	    int mid = start + (end - start) / 2 ;
	    if(nums[mid] > nums[end]) { // <=== if mid greater than end [largest]
		start = mid + 1 ;
	    } else {
		end = mid ;
	    }
	}
```

So search in a rotated array will look like this :
```
public int search(int[] nums, int target) {
	int min = bMin(nums) ;
	// Binary search from min to end
	int found = exoticBSearch(nums, min, nums.length, target);
	if(found == -1) {
	    // if not found from o to min
	    found = exoticBSearch(nums, 0, min, target);
	}
	return found ;
}
```

Further evidence [Video 2](https://youtu.be/flc19LGlCDE)
Practice This approach with [Medium Leetcode 34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

Watch this how we use exotic BS in [this hard problem](https://youtu.be/5PoVGnbju0Y) 
Practice this [Hard problem from leetcode](https://leetcode.com/problems/create-sorted-array-through-instructions/)
