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

#### True approach (Exotic -> Interviewdose ) :
Watch in detailed about this approach in this [Video 1](https://www.youtube.com/watch?v=I6viYY0mS6I&start=52s)

```
	int exoticBSearch(int arr[], int target) {
		int start = 0;
		int end = nums.length ;
		while( start < end) {
			int mid = start + (end - start) / 2 ;
			if( nums[mid] < target) {
					start = mid + 1 ;
			} else  {
					end = mid ;
			}
		}
			
		//return start ; /* this will return the insertion point for a non existing element */
		
		return start ==  nums.length ? -1 : nums[start] == target ? start : -1 ;
	}
```

Further evidence [Video 2](https://youtu.be/flc19LGlCDE)
Practice This approach with [Medium Leetcode 34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

Watch this how we use exotic BS in [this hard problem](https://youtu.be/5PoVGnbju0Y) 
Practice this [Hard problem from leetcode](https://leetcode.com/problems/create-sorted-array-through-instructions/)
