## Least recently used (LRU) Cache

I use to get confused with the name as a least english speaker :)
In Short, this is a Cache replacement algorithm used in computer science and yes computer mimics brain and we forget the things which we don't use or refresh often ! isn't it ?
LRU Cache are designed exactly keeping this in mind. It's one of the most frequently used cache replacement algorithm.

[What is Least Recently Used (LRU) cache](https://en.wikipedia.org/wiki/Cache_replacement_policies#LRU)

Cache replacement algorithms are efficiently designed to replace the cache when the space is full. 
As the name suggests when the cache memory is full, LRU picks the data that is least recently used and removes it in order to make space for the new data.

## Design a recently used (LRU) Cache

Let's design a simple LRU cache that follows the constraints of a LRU cache.

With following use cases:

* LRUCache(int capacity) Initialize the LRU cache with positive size capacity.
* int get(int key) Return the value of the key if the key exists, otherwise return -1.
* void put(int key, int value) Update the value of the key if the key exists. Otherwise, add the key-value pair to the cache.
* If the number of keys exceeds the capacity from this operation, evict the least recently used key.
* The functions get and put must each run in O(1) average time complexity.

To fetch the nodes by key in O(1) time we will use a HashMap and to refresh the nodes position from anywhere to front
and evict the ndoes from the end, DoublyLink list is the best data structure we can use.

In short these are some of the use cases for Doubly LinkLists we have to implement
* Add to head of the list
* Remove node from the list ( to support refresh )
* Evict from the tail of the list when size of the cache crosses the desired
* To refresh the nodes, we need to remove an existing node and put it infront of head

**Here is an implementation for LRU cache:**

Note : We are creating head and tail dummy node with a invalid key and value. 

    //head.next is the real head
    head = new Node(-1, -1) ;
    //tail.prev is the real tail
    tail = new Node(-1, -1) ;
    //attach head and tail
    head.next = tail;
    tail.prev = head ;
    

&#9758; This is a technique that can be used to avoid null check in doubly linklist logic, So that we always insert and remove somewhere from the middle of the list. Also it is very very important to note that we have initialized the head.next = tail and tail.prev = head ; in the constructor with the total size. Add and remove to the map in the add and remove method of the linklist.

Here is a link to practice problem for your next interview : https://leetcode.com/problems/lru-cache/

```
class LRUCache {

    class Node {
        int key;
        int val ;
        Node next ;
        Node prev ;

        Node(int key, int val) {
            this.key = key ;
            this.val = val ;
        }
    }

    int size = 0 ;
    Map<Integer, Node> map = new HashMap<>();

    //head.next is the real head
    Node head = new Node(-1, -1) ;
    //tail.prev is the real tail
    Node tail = new Node(-1, -1) ;

    void addToHead(Node newNode) {
        //it's actually an insert at front

        //stitch right side
        newNode.next = head.next ;
        head.next.prev = newNode ;

        //stitch left side
        head.next = newNode ;
        newNode.prev = head ;

        map.put(newNode.key, newNode) ;
    }

    void remove(Node newNode) {
        Node after = newNode.next ;
        Node before = newNode.prev ;

        before.next = after;
        after.prev = before ;

        map.remove(newNode.key) ;
    }

    void removeFromTail() {
        remove(tail.prev);
    }

    public LRUCache(int capacity) {
        size = capacity ;

        head.next = tail;
        tail.prev = head ;
    }

    public int get(int key) {
        Node node = map.get(key) ;
        if(node != null) {
            remove(node);
            addToHead(node) ;
            return node.val ;
        }
        return -1 ;
    }

    public void put(int key, int value) {
        Node node = map.get(key) ;
        if(node != null) {
            remove(node);
            node.val = value ;
            addToHead(node) ;
        } else {
            Node newNode = new Node(key, value) ;
            addToHead(newNode) ;
            if(map.size() > size) {
                removeFromTail() ;
            }
        }
    }
}
```



