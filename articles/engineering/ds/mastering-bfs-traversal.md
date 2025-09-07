## Master this BFS solution for every BFS problem you write

BFS traversal is solved using Queue. Follow this **exact** approach to write BFS problem. 
It is surpising to see that, even almost all HARD problem with permutaion and combinations can be solved using BFS !!
So pay special attention to this logic.

```

Queue<TreeNode> queue = new ArrayDeque<>();
    queue.offer(root);

    int level = 0 ;
    while (!queue.isEmpty()) {

        int levelSize = queue.size(); // look this size separated
        
        for (int i = 0; i < levelSize; i++) { //use this for loop
            TreeNode currentNode = queue.poll(); //inside loop -> poll()
            
            if (currentNode.left != null) {
                queue.offer(currentNode.left);
            }
            if (currentNode.right != null) {
                queue.offer(currentNode.right);
            }
        }
        level ++ ; //increase the level / step count
    }

```

Refer : https://leetcode.com/problems/coin-change/

```
public int coinChange(int[] coins, int amount) {

        Set<Integer> cache = new HashSet<>() ;
        Queue<Integer> dq = new ArrayDeque<>() ;
        dq.offer(amount) ;
        int level = 0 ;
        while(!dq.isEmpty()) {

            int length = dq.size() ;
            for(int i = 0 ; i < length ; i ++) {

                int target = dq.poll() ;
                if(target == 0) {
                    return level ;
                }

                for(int j = 0 ; j < coins.length ;j++) {
                    int next = target - coins[j];
                    if(next >= 0 && !cache.contains(next)) {
                        dq.offer(next) ;
                        cache.add(next) ;
                    }
                }
            }
            level ++ ;
        }

        return -1 ;
    }
```

Refer : https://leetcode.com/problems/letter-combinations-of-a-phone-number

```

```

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
Above solution is timing out we can optmise it further by following this.

Place two pointers x and y at the left and right ends of the input string s. Advance the pointers inward (x += 1, y -= 1) when  they're not, we'll have to explore the two options of removing the right or left characters separately.

Now we can model this problem as graph traversal. Nodes are defined by the two pointers (x, y) placed at the end of the remaining substring, where s[x] != s[y]. Edges correspond to deletion of a character. Two edges emerge from each node, corresponding to removing the x or the y index. The objective is to find a path with a length less than k to get to a node where x >= y.

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
