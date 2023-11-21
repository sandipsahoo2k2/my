## Binary search

Binary Search is a **searching algorithm** for finding an element's position in a **sorted array**.

In this approach, the element is always searched in the middle of the given array.

==> *Run a loop or recursively test*
* mid  = start + (end - start) / 2
* if array[mid] == target ??

#### Recursive approach :
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

Practice This easy question from [leetcode](https://leetcode.com/problems/binary-search/)



