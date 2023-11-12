<!-- Knowledge Check | Backtracking | pass=100% | Certificate -->
## What's backtracking ?
Backtracking can be defined as an algorithmic technique that considers searching every possible combination to solve a problem.

In simple terms, backtracking is like trying different paths, and when you hit a dead end, you backtrack to the last choice and try a different route. This technique involves finding a solution incrementally by trying **different options** and **undoing** them if they lead to a dead end.

Using backtracking many complex problems dealing with subsets and combinatrics can be solved. If you want to know more in detail on this topic, You may refer this detailed explainations with examples on this topic [here](../../articles/engineering/backtracking_template.md)

### Take this simple test to check your knowledge on this topic
By attempting this assesment ( See to your right or scroll down to attempt the challenge ), You will be able to revise and master the back tracking concepts. It will help you easily attempt problems involving subsets and combinotrics in general.
- You may refer this video with explanation on the [backtracking generic template](https://youtube.com/watch?v=-UhqRVFnwOY) if you are unsure how to solve backtracking questions and time complexities of different approaches.
  
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
