## Least recently used (LRU) Cache

LRU Cache is an algorithm used in many software products e.g. browser, website cache, etc. Computer mimics the brain and we forget the things that we don't use or refresh often! isn't it ?
LRU Cache is designed exactly keeping this in mind. It's one of the most frequently used cache replacement algorithms.

[What is Least Recently Used (LRU) cache](https://en.wikipedia.org/wiki/Cache_replacement_policies#LRU)

Cache replacement algorithms are efficiently designed to replace the cache when the space is full. 
As the name suggests when the cache memory is full, LRU picks the data that is least recently used and removes it in order to make space for the new data.

## Design a Least Recently used (LRU) Cache

Let's design a simple LRU cache that follows the constraints of a LRU cache.

With the following use cases:

* LRUCache(int capacity) Initialize the LRU cache with positive size capacity.
* int get(int key) Return the value of the key if the key exists, otherwise return -1.
* void put(int key, int value) Update the value of the key if the key exists. Otherwise, add the key-value pair to the cache.
* If the number of keys exceeds the capacity from this operation, evict the least recently used key.
* The functions get and put must each run in O(1) average time complexity.

In Java there is an implementation of HashMap which is **_LinkedHashMap_** has this support already. Even in an interview environment if time/interviewer permits speak about it and use it too. Look at the method **_removeEldestEntry_** implementation in the below example. Also see the constructor's last parameter **accessOrder** - the ordering mode - true for access-order, false for insertion-order .

    LinkedHashMap cache = new LinkedHashMap<>(size, 0.75f, true) {
            @Override
            protected boolean removeEldestEntry(Map.Entry<Integer, Integer> eldest) {
                return size() > capacity;
            }
        };

To fetch the nodes by key in O(1) time we will use a HashMap to refresh the nodes position from anywhere to the front
and evict the nodes from the end, DoublyLink list is the best data structure we can use.

In short, these are some of the use cases for Doubly LinkLists we have to implement
* Add to the head of the list
* Remove node from the list ( to support refresh )
* Evict from the tail of the list when the size of the cache crosses the desired
* To refresh the nodes, we need to remove an existing node and put it in front of head

**Here is an implementation for LRU cache:**

Note: _We are creating head and tail dummy node with an invalid key and value. Never change the head and tail in this implementation they will always point to the dummy node and we return head.next or tail.prev if we must._

    //head.next is the real head
    head = new Node(-1, -1) ;
    //tail.prev is the real tail
    tail = new Node(-1, -1) ;
    //attach head and tail
    head.next = tail;
    tail.prev = head ;
    

&#9758; This is a technique that can be used to avoid null check in doubly linklist logic, _So that we always insert and remove somewhere from the middle of the list_. Also it is very very important to note that we have initialized the head.next = tail and tail.prev = head ; in the constructor with the total size. Add and remove to the map in the add and remove method of the linklist.

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

If you understand this can you build a LFU cache? Here is a link to the practice problem https://leetcode.com/problems/lfu-cache/

## Least Frequently Used (LFU) Cache
LFU Cache is very similar to LRU cache, the difference is it keeps track of time and Frequency of the key and removes the key with minimum frequency if there are multiple entries at that time.


