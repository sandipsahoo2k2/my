<!-- Knowledge Check | Backtracking | pass=100% | Certificate -->
## General approach solving questions using backtracking
Backtracking can be defined as an algorithmic technique that considers searching every possible combination to solve a problem.

In simple terms, backtracking is like trying different paths, and when you hit a dead end, you backtrack to the last choice and try a different route. This technique involves finding a solution incrementally by trying **different options** and **undoing** them if they lead to a dead end.

By attempting this assesment, You will be able to master the back tracking concepts and will be able to easily attempt problems involving subsets and combinotrics.
- You may refer this video with explanation on the [backtracking generic template](https://youtube.com/watch?v=-UhqRVFnwOY) to help you clarifying this assessment.

- You may refer the detailed explainations of backtracking with examples on this topic [here](../../articles/engineering/backtracking_template.md)

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
