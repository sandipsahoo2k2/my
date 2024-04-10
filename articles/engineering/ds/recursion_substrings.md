## Find all substrings for a given array using recursion
Recursion problems are mind bending isn't it ? Here is how master recursion.
Recursion is nothing but calling the same method with a base case to return.

**A Forloop :**

Think about a forloop and how would you convert it to a recursive method ?
```
for(int i = 0; i < nums.length ; i++) {
  //print elements
}
//print result from the for loop
```

**Replace Forloop with a recursion:**

Look at this example how a forloop can be transformed to a recursive method. 
Just call the same method increasing the index by 1 and return when the index = given array length.

```
void forLoop(int[] nums, int index, List<Integer> list) {

        if(index == nums.length) {
            return ;
        }

        list.add(nums[index]); //add current element to list
        forLoop(nums, index + 1, list);
    }
```

**Print sublist for every iteration:**

Once you know the above way to write a forloop, if you are asked to write print the list in every step for the given loop 
then if we add a result array to the above code and add the list for each iteration, job is done.

```
void forLoop(int[] nums, int index, List<Integer> list, List<List<Integer>> result) {

        if(index == nums.length) {
            return ;
        }

        result.add(list); //print subList every iteration

        list.add(nums[index]);
        forLoop(nums, index + 1, new ArrayList<>(list), result);
    }
```

**Print all substrings for a given array :**

If you understood the above structures and understand how these recursive calls work. 
Now printing all substrings for a given array using recursion can be wriiten as below.

```
void allSubstring(int[] nums, List<List<Integer>> result) {
        for(int i = 0; i < nums.length ; i++) { //add another for loop
            forLoop(nums, i, new ArrayList<>(), result); //call the recursive forLoop
        }
    }
```


Why I am talking about this here !
It's one of the most important concept you may need to know for solving any subset or substrings problem in an interview.
e.g look at this subset program using recursion. [Read more about subsets and backtracking](https://interviewdose.com/i/articles/engineering/ds/subsets.md).

```
public void backtrack(int[] nums, int start, List<Integer> temp, List<List<Integer>> result) {
        
        result.add(temp) ;
        
        if(start == nums.length) {
            return ;
        }

        for(int i = start; i < nums.length ; i++) {
            temp.add(nums[i]) ;
            backtrack(nums, i + 1, new ArrayList<>(temp), result) ;
            temp.remove(temp.size() - 1) ;
        }
        
    }
```
