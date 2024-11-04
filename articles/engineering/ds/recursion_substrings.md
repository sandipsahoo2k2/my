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

**Print all substrings for a given array : Option - 1**

If you understood the above structures and understand how these recursive calls work. 
Now printing all substrings for a given array using recursion can be wriiten as below.


```
void allSubstring(int[] nums, List<List<Integer>> result) {
        for(int i = 0; i < nums.length ; i++) { //add another for loop
            forLoop(nums, i, new ArrayList<>(), result); //call the recursive forLoop
        }
    }
```

If you understood until this far next is how can you take this idea and [solve any DFS problem](https://www.youtube.com/watch?v=5apYEdUv_O4&t=10s).

**Print all substrings for a given array : Option - 2 - useful for number array problems**

We print 1 to n - 1 length substrings in each iteration
substring reads from left side starting from 0th index until j ( j+ 1 )

Time complexity O(NSquare)
```
void allSubstring(String given) {
  for(int i = 0 ; i < given.length() ; i ++) {
    for(int j = i; j < given.length() ; j ++) { //<== look at the conditon how similar
      System.out.println(given.substring(i, j + 1)) ; // <== from i to j + 1 
    }
  }
```

**Print all substrings for a given array : Option - 3 - useful for string / leetcode problems**

We print 1 to n - 1 length substrings in each iteration
substring reads from right towards 0th index until i ( i + 1 )

```
void allSubstring(String given) {
  for(int i = 0 ; i < given.length() ; i ++) {
    for(int j = i; j >= 0 ; j --) {
      System.out.println(given.substring(j, i + 1)) ; // <= from j to i + 1
    }
  }
```

&#9758; _Why I am talking about recursion and this particular program here !_

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
Learn in depth and solve any subset problems &#9758; https://www.youtube.com/watch?v=-UhqRVFnwOY
Some leetcode problems for reference : https://youtube.com/watch?v=siNWNRgtlEk

**Generate all combinations of well-formed parentheses:**

Now as you understood how backtracking works, generating all possible valid parentheses should not be difficult.
keeping few cases in mind e.g
* when open braces = closing braces return/add result
* run backtrack to construct open braces until given target n
* run backtrack to construct closing braces for each open bracket

```
Stack<String> stk = new Stack<>() ;
    public void helper(int total , int open, int close, List<String> result) {

        if(open == total && open == close) {
            result.add(String.join("", stk)) ;
            return ;
        }

        if(open < total) {
            stk.push("(");
            helper(total, open + 1, close, result) ;
            stk.pop();
        }

        if(close <  open) {
            stk.push(")");
            helper(total, open, close + 1, result) ;
            stk.pop();
        }
    }

    public List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList<>();
        helper(n, 0, 0, result) ;
        return result ;
    }
```

Practice link : https://leetcode.com/problems/generate-parentheses/
