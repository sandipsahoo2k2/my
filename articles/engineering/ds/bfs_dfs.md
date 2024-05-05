<!-- -->
## Graph traversal approach ( DFS and BFS )
Leetcode practice link : https://leetcode.com/problems/valid-palindrome-iii

Staright forward BFS solution by deleting 1 character and exploring the nodes.

```
class Solution {

    boolean isValidPalindrome(String s, int i , int j) {
        while(i < j) {
            if(s.charAt(i) != s.charAt(j)) {
                return false ;
            }
            i++ ;
            j-- ;
        }
        return true;

    }

    public boolean isValidPalindrome(String s, int k) {
        Queue<String> dq = new ArrayDeque<>() ;
        dq.offer(s) ;
        Set<String> visited = new HashSet<>();
        visited.add(s) ;

        int step = 0 ;
        while(!dq.isEmpty()){
            int size = dq.size() ;
            for(int j = 0; j < size ; j++) {
                String node = dq.poll() ;

                if(step > k) {
                    return false ;
                }

                if(isValidPalindrome(node, 0, node.length() -1)) {
                    return true ;
                }

                for(int i = 0 ;  i < node.length() ; i++) {
                    String newString = node.substring(0,i) + node.substring(i+1) ;
                    if(!visited.contains(newString)) {
                        dq.offer(newString) ;
                        visited.add(newString);
                    }
                }
            }
            step ++ ;
        }
        return false ;
    }
}
```

Place two pointers l and r at the left and right ends of the input string s. Advance the pointers inward (i += 1, j -= 1) while the characters they're pointing to are equal. And when they're not, we'll have to explore the two options of removing the right or left characters separately.

Model this problem as graph traversal. Nodes are defined by the two pointers (i, j) placed at the end of the remaining substring, where s[i] != s[j]. Edges correspond to deletion of a character. Two edges emerge from each node, corresponding to removing the i or the j index. The objective is to find a path with a length less than k to get to a node where i >= j.

```
public boolean isValidPalindrome(String s, int k) {
    Set<String> visited = new HashSet<>() ;
    Queue<int[]> dq = new ArrayDeque<>() ;

    dq.offer(new int[]{0, s.length() - 1}) ;
    visited.add(0 + "" + (s.length() - 1)) ;

    int step = 0 ;
    while(!dq.isEmpty()) {
        int size = dq.size() ;
        for(int i = 0 ; i < size ; i++) {
            int[] node = dq.poll() ;

            int x = node[0] ;
            int y = node[1] ;


            if(step > k) { //condition
                return false ;
            }

            while(x < y){
                if(s.charAt(x) != s.charAt(y)){
                    String key = (x+1) + "" +  y ;
                    if(!visited.contains(key)){
                        dq.offer(new int[]{x+1, y});
                        visited.add(key);
                    }

                    key = x + "" +  (y - 1);
                    if(!visited.contains(key)){
                        dq.offer(new int[]{x, y-1});
                        visited.add(key);
                    }
                    break ; //important remember
                }
                x ++ ;
                y -- ;
            }
            if(x >= y) { //condition check
                return true ;
            }
        }
        step ++ ;
    }      
    return false ;
}
```
