<!-- Knowledge Check | Backtracking | pass=100% | Certificate -->
## What's backtracking ?
Backtracking can be defined as an algorithmic technique that considers searching every possible combination to solve a problem.

In simple terms, backtracking is like trying different paths, and when you hit a dead end, you backtrack to the last choice and try a different route. This technique involves finding a solution incrementally by trying **different options** and **undoing** them if they lead to a dead end.

Using backtracking many complex problems dealing with subsets and combinatrics can be solved. You may [**refer this article**](https://interviewdose.com/articles/engineering/backtracking_template) on detailed explainations with examples on this subject.

### Take this simple test, check your knowledge
By attempting this assesment, You will be able to revise and master the backtracking concepts. It will help you easily attempt problems involving subsets and combinotrics in general.

- You may refer this video with explanation before starting the challenge [backtracking generic template](https://youtube.com/watch?v=-UhqRVFnwOY)
- See to your right on desktop or scroll down in mobile to find the link for the challenge
  
#### General backtracking approcah and template

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

**Solve Subsets** :

```
public List<List<Integer>> subsets(int[] nums) {
    List<List<Integer>> list = new ArrayList<>();
    Arrays.sort(nums);
    backtrack(list, new ArrayList<>(), nums, 0);
    return list;
}
```

**Solve Subsets with duplicate inputs** :

```
public List<List<Integer>> subsetsWithDup(int[] nums) {
    List<List<Integer>> list = new ArrayList<>();
    Arrays.sort(nums);
    backtrack_dup(list, new ArrayList<>(), nums, 0);
    return list;
}
```
