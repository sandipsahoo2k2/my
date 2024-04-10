## Find all Subsets of a given array of numbers

This is one of the most frequently asked interview question in a coding interview.
There are many different ways this problem can be solved, but if you start from the powerset solution approach to knapsack approach, 
you will enable yourself in solving multiple different types of subsets problem.
I am sharing two approach that you should or must know for an interview environment here. 

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

If you closely look at the above solution and resultsin each step we are creating 2 times mores sets from the previous result.
```
        []              <== start with empty
       [][1]            <== add 1
     [][1][2][1,2]      <== add 2
[][1][2][1,2][3][1,2,3] <== add 3
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

Refer [this artcile](https://interviewdose.com/i/articles/engineering/backtracking_template.md) for in depth knowledge on different backtracking techniques.

```
public void backtrack(int[] nums, int start, List<Integer> temp, List<List<Integer>> result) {

        result.add(new ArrayList<>(temp)) ;
        
        if(start >= nums.length) {
            return ;
        }

        for(int i = start; i < nums.length ; i++) {
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

I tried my best to show you how the algorithm evolved and shared [all different ways to return subsets](https://www.youtube.com/watch?v=-UhqRVFnwOY).
