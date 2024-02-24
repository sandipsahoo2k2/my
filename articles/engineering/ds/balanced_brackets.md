## Balanced Brackets

A string containing bracket characters is said to be balanced if:

1. A matching closing bracket occurs to the right of each corresponding opening bracket
2. Brackets enclosed within balanced brackets are also balanced
3. It does not contain any non-bracket characters

<u>Example:</u>   [Tune to this Poddcast](https://www.youtube.com/playlist?list=PLZhF5vHIhxf3QFZRRS2jZLf2ksiBhkd0Z)

* (){}[] - "This contains a [balanced bracket]"
* [[] {}} - “This [[does not] contain a balanced bracket”
* ({}) - “This ( is an {interesting}) example with multiple brackets”  

<u>**Solution Approach :**</u>

We can use a Stack data structures to solve such problems.
1. <u>Run a loop on each chacarter on the given string</u>

   **if**

       Current character is an opening bracket
   	‘(‘ or ‘{‘  or ‘[‘ then push it to stack.
       
    **else**
       
       _if_ the stack is not empty_
  
   		pop the stack
   		if popped character from the stack is not the opening pair
   		of the current bracket, then its not balanced
       
       _else_
     
   		We are now looking at a closing bracket without a opening bracket
   		on it's left, So its not balanced
   
3. After the loop check if stack is not empty, then we are left with some opening brackets, so not balanced.
4. Finally If stack is empty, The string has balanced brackets.

[Watch this for deeper understanding on this solution approach](https://youtu.be/VWGk_Mo_gRU?si=_CyZnsBhWjCTkG31)

Practice this [leetcode Easy Question](https://leetcode.com/problems/valid-parentheses/)

#### Some Techniques to apply :
Before the solution, Remember few _**simple techniques**_ for solving such problems.

* Be mindful about stack.empty() -> not balanced case
* If only One type of balanced brackets e.g '(' ')' used, then use a stackCounter instead of a Stack.
* Sometimes They can ask you to balance the given string -> then mark invalid characters with * and solve.
* Sometimes they want you to count max or min Use a Stack for keeping the index and initisialised with -1 index.

#### InterviewDose Solution
```
boolean isBalanced(String s) {
	if(s == null || s.length() == 0) {
  		Return true ;
  	}
  
  	Stack<Character> st = new Stack<>() ;
  
  	for(int i = 0 ; i < s.length() ; i ++) {

  		char c = s.charAt(i) ;
  		if ( c == ‘(‘ ) {
  			st.push(‘)’) ;
  		} else if ( c== ‘{‘ ) {
  			st.push(‘}’) ;
  		} else if ( c== ‘[‘ ) {
        		st.push(‘]’) ;
		} else {
  	    		if(st.isEmpty()) {
  		    		return false ;
  	    		}
  	  		if( c != st.pop()) {
        			return false ;
			}
    		}
  	}
  	return st.size() == 0 ;
}
```

**Few More Practice questions from leetcode and ID solutions :**

* Watch This podcast : https://www.youtube.com/playlist?list=PLZhF5vHIhxf3QFZRRS2jZLf2ksiBhkd0Z

* [Practice Leetcode 32](https://leetcode.com/problems/longest-valid-parentheses/)

* [Practice this Medium Leetcode Problem](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/) -- [Watch the Solution](https://youtu.be/slkTFARW4Pk?si=OffRL-ywtG5iLLa5) 

* [Practice this Medium Leetcode Problem](https://leetcode.com/problems/minimum-insertions-to-balance-a-parentheses-string/) -- [Watch the Solution](https://youtu.be/LScsC-C5gvg?si=n-nd6YU2YkAjYaXb)
