## Union Find

[Union find](https://www.youtube.com/watch?v=ayW5B2W9hfo) is a data structure used in graph problems to join disjoint sets/graphs and do some operation on a common characteristics.

In simple terms try to visualise this like as if, you have more than one groups with different roots ( disjoint sets )
and you want to group them together without loosing the root/parent property then use this strategy to union them into a single group.

Use `Find` method to correctly find the true parent/representative of a node
```
String find(Node node) { //return if it's true parent
  //if node's parent is not itself then recursively call to find it's parent
  return parents.get(node) == node ? node : find(parents.get(node)); 
}
```

Use `Union` to group two parents into one by assigning one of the root ( parent / representative ) as the parent for the other group's representative
```
String union(Node p, Node q) {
  Node root1 = find(p) ; //root1 is nothing but the true parent
  Node root2 = find(q) ;
  if(root1 != root2) {
    parents.put(root1, root2) ;
  }
}
```

Leetcode problem : https://leetcode.com/problems/accounts-merge/ is a classic example where you can use this union find algorithm find the result.

This is how to solve this problem :
1. Initialise the parents map for each email to itself
2. Update each emails parents to it's group head/ representative -> to it's first email
3. Once you have the group head set properly, just create a uninon with a map<Stirng, List/TreeSet<String>>

```java
class Solution {

    Map<String, String> owner = new HashMap<>();
    Map<String, String> parents = new HashMap<>();

    private String find(String s) { //return if its true parent
        return parents.get(s) == s ? s : find(parents.get(s));
    }

    public List<List<String>> accountsMerge(List<List<String>> acts) {
        //initialize parent of x to itself
        for (List<String> a : acts) {
            for (int i = 1; i < a.size(); i++) {
                parents.put(a.get(i), a.get(i));
            }
        }

        //create disjoint sets / groups with same parent/representative
        for (List<String> a : acts) {

            //String rep = find(a.get(1)); <-- why ?

            /* ---> Why not String rep = a.get(1); ? <-- what if this exists in another group */

            String rep = find(a.get(1)); // < -- that's why get the true parent for each email
            for (int i = 2; i < a.size(); i++){
                parents.put(find(a.get(i)), rep);
            }
        }

        //create union
        Map<String, TreeSet<String>> unions = new HashMap<>();
        for(List<String> a : acts) {
            String rep = find(a.get(1));
            TreeSet nodes = unions.getOrDefault(rep, new TreeSet<>());
            for (int i = 1; i < a.size(); i++){
                nodes.add(a.get(i));
            }
            unions.put(rep, nodes); //sorted group by parents map
            owner.put(a.get(i), a.get(0));
        }

        //create result
        List<List<String>> res = new ArrayList<>();
        for (String parent : unions.keySet()) {
            List<String> emails = new ArrayList(unions.get(parent));
            emails.add(0, owner.get(parent));
            res.add(emails);
        }
        return res;
    }
```


