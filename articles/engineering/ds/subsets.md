## Find all Subsets of a given array of numbers

This is one of the most frequently asked interview question in a coding interview.
There are many different ways this problem can be solved, but if you start from the powerset solution approach to knapsack approach, 
you will enable yourself in solving multiple different types of subsets problem with ease.
I am sharing two approach that you should or must know for an interview environment here.

Note : Time complexity for the loop is 2^n and we copy n elements each time hence 
Time = O(N*2^N) 
Space = O(N)

**Cascading approach :**

```
public List<List<Integer>> subsets(int[] nums) {

        List<List<Integer>> result = new ArrayList<>() ;
        result.add(new ArrayList<>()); //must add an empty list for []
        for(int i : nums) { //[1,2,3]
            List<List<Integer>> subSets = new ArrayList<>() ; //step subsets to add to result
            for(List<Integer>  list : result){
                List<Integer> temp = new ArrayList<>(list);//must create a copy
                temp.add(i) ;
                subSets.add(temp) ;
            }
            result.addAll(subSets) ;//[],[1],[1,2]
        }
        return result ;
    }
```

If you closely look at the above solution and results in each step we are creating 2 times mores sets from the previous result.
```
              []                  <== start with empty
             [][1]                <== add 1
         [][1][2][1,2]            <== add 2
[][1][2][1,2][3][1,3][2,3][1,2,3] <== add 3
```
Hence 2^N elements in total we create. Do you see it is forming a binary tree structure right ?
That means the resultsets can also created using a binary tree traversal technique. which is nothing but our knapsack approach described below.
If you closely see each step what we can say is we are either adding an element from a possible choice or not adding that elelemnt
Look at the code below how this solution can be written using a knapsack approach (is n't it looking like a inOrder traversal ? ) 

**Knapsack approach :**
```
public void knapsack(int[] nums, int index, List<Integer> subset, List<List<Integer>> result) {

        if(index == nums.length) {
            result.add(new ArrayList<>(subset)) ;
            return ;
        }

        knapsack(nums, index + 1, new ArrayList<>(subset), result) ; //recurse without adding the current element
        subset.add(nums[index]) ; //see we added the element
        knapsack(nums, index + 1, new ArrayList<>(subset), result) ; //recurse adding the current element
    }

    public List<List<Integer>> subsets(int[] nums) {

        List<List<Integer>> result = new ArrayList<>() ;
        knapsack(nums, 0 , new ArrayList<>(), result) ;
        return result ;
    }
```

**Backtracking approach:**

Refer [this article](https://interviewdose.com/i/articles/engineering/backtracking_template.md) for in depth knowledge on different backtracking techniques.

```
public void backtrack(int[] nums, int start, List<Integer> temp, List<List<Integer>> result) {

        result.add(new ArrayList<>(temp)) ;
        
        if(start >= nums.length) {
            return ;
        }

        for(int i = start; i < nums.length ; i++) {

            //<== Here check conditions when required
            //<== e.g isPalindrome to list all palindrome combinations

            temp.add(nums[i]) ;
            backtrack(nums, i + 1, temp, result) ;
            temp.remove(temp.size() - 1) ;
        }
        
    }

    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>() ;
        backtrack(nums, 0, new ArrayList<>(), result) ;
        return result ;
    }
```

I tried my best to show you how the algorithm evolved and shared here [all different ways to return subsets](https://www.youtube.com/watch?v=-UhqRVFnwOY).

Some leetcode problems solved using these templates : https://youtube.com/watch?v=siNWNRgtlEk

**Backtracking approach to find permutations: Time O(n*n!), Space O(n)**

If you look closely permutations is list of subsets by swaping numbers with all elements of the array.
By twiking the above backtracking code little bit we can form all permutations.

Note : Time complexity for the recursion is n! and we copy n elements each time hence 
Time = O(N*N!) 
Space = O(N)

* return or add to result only when the size = arr.length
* start the for loop from zero to length always because it contains all elements in the subset
* skip the element if it is already present in the subset

Note : For Combination, return when size = k.

```
                        [1,2,3]

        [1,2,3]		[2,1,3]		[3,1,2]

[1,2,3]	[1,3,2]     [2,1,3][2,3,1]      [3,1,2][3,2,1] //<== 3! permutations

```

This is how permute code looks :

```
void backtrack(int[]nums, int start, List<Integer> temp, List<List<Integer>> result) {
        if(temp.size() == nums.length) { //<== See when size == length
            result.add(temp) ;
            return ;
        }

        for(int i = 0; i < nums.length;i++) { // <== start always from zero
            if (temp.contains(nums[i])) continue ; // <== skip if element exists in the subset
            temp.add(nums[i]);
            backtrack(nums, i + 1, new ArrayList<>(temp), result);
            temp.remove(temp.size() - 1) ;
        }
    }

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>() ;
        backtrack(nums, 0, new ArrayList<>(), result);
        return result;
    }
```

**Backtracking-ii approach with swap find permutations: Time O(n*n!), Space O(n)**
using swap method we can write this code too here is the example

```
class Solution {
    public void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    public void backtrack(int[] arr, int start, List<List<Integer>> result) {
        if (start == arr.length) {
            result.add(Arrays.stream(arr).boxed().collect(Collectors.toList()));
        }

        for (int i = start; i < arr.length; i++) {
            swap(arr, start, i); //swap current with next
            backtrack(arr, start + 1, result); //<== recurse next element
            swap(arr, start, i); //backtrack
        }
    }

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>() ;
        backtrack(nums, 0, result) ;
        return result ;
    }
}

```

<img width="616" alt="image" src="https://github.com/sandipsahoo2k2/my/assets/5547869/4f142849-e8b6-45b8-9496-9decec3b1de5">


To know more on different backtracking techniques on permutations and combinations read https://interviewdose.com/articles/engineering/backtracking_template
