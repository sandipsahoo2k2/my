## Balanced Brackets

A string containing bracket characters is said to be balanced if:

1. A matching closing bracket occurs to the right of each corresponding opening bracket
2. Brackets enclosed within balanced brackets are also balanced
3. It does not contain any non-bracket characters

<u>Example:</u>

* "This contains a [balanced bracket]"
* “This [[does not] contain a balanced bracket”
* “This ( is an {interesting}) example with multiple brackets”

<u>**Solution Approach :**</u>

We can use a Stack data structures to solve such problems.
1. <u>Run a loop on each chacarter on the given string</u>

   **if**

       Current character is a opening bracket - ‘(‘ or ‘{‘  or ‘[‘ then push it to stack.
       
    **else**
       
       _if_ the stack is not empty_
  
   		pop the stack
   		if popped character from the stack is not the opening pair of the current bracket, then its not balanced
       
       _else_
     
   		We are now looking at a closing bracket without a opening bracket on it's left
         	So its not balanced
   
3. After the loop check if stack is not empty, then we are left with some opening brackets, so not balanced.
4. Finally If stack is empty, The string has balanced brackets.

#### InterviewDose approach :
Before the solution, Remember few simple techniques for solving such problems.

* If only One type of balanced brackets e.g '(' ')' used, then use a stackCounter instead of a Stack.
* Sometimes They can ask you to balance the given string -> then mark invalid characters with * and solve.
* Sometimes they want you to count max or min Use a Stack for keeping the index and initisialised with -1 index.

#### Solution
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

Practice This approach with [Easy Leetcode 704](https://leetcode.com/problems/binary-search/)

Further evidence [Video 2](https://youtu.be/flc19LGlCDE)