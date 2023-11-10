<!-- Knowledge Check | Title | pass=100% | Certificate -->
## General approach solving questions using backtracking
Backtracking can be defined as an algorithmic technique that considers searching every possible combination to solve a problem.

In simple terms, backtracking is like trying different paths, and when you hit a dead end, you backtrack to the last choice and try a different route. 
This technique involves finding a solution incrementally by trying **different options** and **undoing** them if they lead to a dead end.

In this article, we’ll explore the basics of backtracking, how it works, and how it can help solve all sorts of challenging problems. 
It’s like a method for finding the right way through a complex choices.

Following is an example of a backtracking method, I would recomend to understand and remember these method as much as you can.
back track from definition as you might have seen that its recursive.

- Refer this video with explanation on the [generic template](https://youtube.com/watch?v=-UhqRVFnwOY) to solve any backtracking problem.
- I would also highly recommend to watch this video by [Abdul Bari](https://www.youtube.com/watch?v=DKCbsiDBN6c) to understand how back tracking works.


#### The backtracking template

1. general backtracking
```
private void backtrack(List<List<Integer>> list , List<Integer> tempList, int [] nums, int start){
    list.add(new ArrayList<>(tempList));
    for(int i = start; i < nums.length; i++){
        tempList.add(nums[i]);
        backtrack(list, tempList, nums, i + 1);
        tempList.remove(tempList.size() - 1);
    }
}
```

2. backtracking with duplicates
```
private void backtrack_dup(List<List<Integer>> list, List<Integer> tempList, int [] nums, int start){
    list.add(new ArrayList<>(tempList));
    for(int i = start; i < nums.length; i++){
        if(i > start && nums[i] == nums[i-1]) continue; // skip duplicates
        tempList.add(nums[i]);
        backtrack(list, tempList, nums, i + 1);
        tempList.remove(tempList.size() - 1);
    }
}
```

**Solve Subsets** : https://leetcode.com/problems/subsets/

```
public List<List<Integer>> subsets(int[] nums) {
    List<List<Integer>> list = new ArrayList<>();
    Arrays.sort(nums);
    backtrack(list, new ArrayList<>(), nums, 0);
    return list;
}
```

**Solve Subsets with duplicate inputs** : https://leetcode.com/problems/subsets-ii/

```
public List<List<Integer>> subsetsWithDup(int[] nums) {
    List<List<Integer>> list = new ArrayList<>();
    Arrays.sort(nums);
    backtrack_dup(list, new ArrayList<>(), nums, 0);
    return list;
}
```

**Solve Permutations** : https://leetcode.com/problems/permutations/

```
public List<List<Integer>> permute(int[] nums) {
   List<List<Integer>> list = new ArrayList<>();
   // Arrays.sort(nums); // not necessary
   backtrack(list, new ArrayList<>(), nums);
   return list;
}

private void backtrack(List<List<Integer>> list, List<Integer> tempList, int [] nums){
   if(tempList.size() == nums.length){
      list.add(new ArrayList<>(tempList));
   } else{
      for(int i = 0; i < nums.length; i++){ 
         if(tempList.contains(nums[i])) continue; // element already exists, skip
         tempList.add(nums[i]);
         backtrack(list, tempList, nums);
         tempList.remove(tempList.size() - 1);
      }
   }
}
```

**Solve Permutations with duplicate inputs** : https://leetcode.com/problems/permutations-ii/

```
public List<List<Integer>> permuteUnique(int[] nums) {
    List<List<Integer>> list = new ArrayList<>();
    Arrays.sort(nums);
    backtrack_dup(list, new ArrayList<>(), nums, new boolean[nums.length]);
    return list;
}

private void backtrack(List<List<Integer>> list, List<Integer> tempList, int [] nums, boolean [] used){
    if(tempList.size() == nums.length){
        list.add(new ArrayList<>(tempList));
    } else{
        for(int i = 0; i < nums.length; i++){
            if(used[i] || i > 0 && nums[i] == nums[i-1] && !used[i - 1]) continue;
            used[i] = true; 
            tempList.add(nums[i]);
            backtrack(list, tempList, nums, used);
            used[i] = false; 
            tempList.remove(tempList.size() - 1);
        }
    }
}
```

**Combination Sum** : https://leetcode.com/problems/combination-sum/

```
public List<List<Integer>> combinationSum(int[] nums, int target) {
    List<List<Integer>> list = new ArrayList<>();
    Arrays.sort(nums);
    backtrack(list, new ArrayList<>(), nums, target, 0);
    return list;
}

private void backtrack(List<List<Integer>> list, List<Integer> tempList, int [] nums, int remain, int start){
    if(remain < 0) return;
    else if(remain == 0) list.add(new ArrayList<>(tempList));
    else{ 
        for(int i = start; i < nums.length; i++){
            tempList.add(nums[i]);
            backtrack(list, tempList, nums, remain - nums[i], i); // not i + 1 because we can reuse same elements
            tempList.remove(tempList.size() - 1);
        }
    }
}
```

**Combination Sum (can't reuse same element)** : https://leetcode.com/problems/combination-sum-ii/

```
public List<List<Integer>> combinationSum2(int[] nums, int target) {
    List<List<Integer>> list = new ArrayList<>();
    Arrays.sort(nums);
    backtrack(list, new ArrayList<>(), nums, target, 0);
    return list;
    
}

private void backtrack(List<List<Integer>> list, List<Integer> tempList, int [] nums, int remain, int start){
    if(remain < 0) return;
    else if(remain == 0) list.add(new ArrayList<>(tempList));
    else{
        for(int i = start; i < nums.length; i++){
            if(i > start && nums[i] == nums[i-1]) continue; // skip duplicates
            tempList.add(nums[i]);
            backtrack(list, tempList, nums, remain - nums[i], i + 1);
            tempList.remove(tempList.size() - 1); 
        }
    }
}
```

**Palindrome Partitioning** : https://leetcode.com/problems/palindrome-partitioning/

```
public List<List<String>> partition(String s) {
   List<List<String>> list = new ArrayList<>();
   backtrack(list, new ArrayList<>(), s, 0);
   return list;
}

public void backtrack(List<List<String>> list, List<String> tempList, String s, int start){
   if(start == s.length())
      list.add(new ArrayList<>(tempList));
   else{
      for(int i = start; i < s.length(); i++){
         if(isPalindrome(s, start, i)){
            tempList.add(s.substring(start, i + 1));
            backtrack(list, tempList, s, i + 1);
            tempList.remove(tempList.size() - 1);
         }
      }
   }
}

public boolean isPalindrome(String s, int low, int high){
   while(low < high)
      if(s.charAt(low++) != s.charAt(high--)) return false;
   return true;
}
```
