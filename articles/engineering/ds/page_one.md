## Why page one for java engineers ?
Sometimes what looks simple is hard in an interview environment, so I thought adding few important basics that may be helpful should I add here.

If your preferred language to code is java ( not python ) then you need to remember few basics mentioned below ( mostly for arrays operation ). 

&#9758; Lets start with a **random()** method in java, it's one of the rarely used method the importance of it might be missed easily .  
Math.random() returns a double value between 0 (including) and 1 (excluding). Use it whenever there is a problem with picking index or values with some probablity. For example if you want to find a a number between 0 to Size ( MaxValue ) with equal _probablity_ then use Math.random() * Size .

* Write a random Function to that returns 0 or 1 with equal probability 
    int rand50()
    {
        // rand() function will generate odd or even 
        // number with equal probability. If rand() 
        // generates odd number, the function will 
        // return 1 else it will return 0. 
        return (int) (10 * Math.random()) & 1;
    }

Now lets take another example.   
Given an input list of values [1, 9], when we pick up a number out of it, how will we make sure that the chance that 9 times out of 10 we should pick the number 9 as the answer ? --> You can do so by building a prefixSum array which is [1,10] and search the insertion point or range where 9 will exists right. 

So if you are asked to pick an index between 0 to n with with probability equal to their weight. then build a prefixSum array and search the target is Math.random() * totalSum. Then search this target in the prefixSum array. Solve this [leetcode problem](https://leetcode.com/problems/random-pick-with-weight) to have clear idea on such a problem.

&#9758;Here is a simple program to do **batch processing** for a job. This is actually a very practical problem that we build time to time.

Write a method to count number of inputs in each bucket that you create according to their face value.
So e.g If given facevalue of an input is 53 with bucket_size = 10 then it will go to the 6th bucket and any 
input which can't be mapped to a bucket will go to the last bucket. Here is the solution to this problem.

```
public static void batch(int[] inputs, int totalBuckets, int bucket_size) {

        Map<Integer, List<Integer>> map = new HashMap<>() ;
        for(int l : inputs) {
            List<Integer> list = map.getOrDefault(l, new ArrayList<>()) ;
            list.add(l) ;
            map.put(l , list) ;
        }

        int buckets[] = new int[totalBuckets + 1] ;
        for(Integer key : map.keySet()) {
            int row = key / bucket_size ;
            int col = key % bucket_size ;
            int finalBucket = row ;
            if(row > totalBuckets - 1) {
                finalBucket = buckets.length - 1;
            }
            buckets[finalBucket] += map.get(key).size() ;
        }
    }
```

Most important take away from this problem is _when you devide by the bucket_size you get the index_ of the bucket.
You might be sometimes asked which row and column the input will go and sit then

> row = key / bucket_size
> 
> col = key % bucket_size

2. For **sorting** ararys with premitive which is quite common use Arrays.sort(anArray) but for reverse sort its not possible even with Arrays.sort(data, Collections.reverseOrder()) so use Arrays.stream(anArray).boxed().toArray(Integer[]::new) then sort.
   
3. Remember the syntax for inbuilt **binarySearch(anArray)** method if time doesn't permit use this method - when you are solving a big problem.

4. Always remember to check the index is bound inside the window in a **while loop** -> while(i >= 0 && i < arr.length )

5. To **convert a list** _to two dimentional array_ you can use toArray(new int[0][]) method <= look at the syntax.

6. To **convert a list** _to one dimentional array_ of int -> `list.stream().mapToInt(i -> i).toArray()`

7. When ever you need to use a frequency characters for english alphabets use int[] charFrequency = new int[128] <--- size = 128 because all valid characters will fit within ascii value 128 including lower case, upper case and numbers.
   
8. You must know how to create numbers from string and also how to do add operations on string chars. [Practice this problem](https://leetcode.com/problems/add-strings)
    
   > e.g where x1 = '2' and x2 = '8'
   > 
   > int value = (x1 + x2 + carry) % 10;
   > 
   > carry = (x1 + x2 + carry) / 10;
   > 
```java
    public String addStrings(String num1, String num2) {
        StringBuilder res = new StringBuilder();

        int carry = 0;
        int p1 = num1.length() - 1;
        int p2 = num2.length() - 1;
        while (p1 >= 0 || p2 >= 0) {
            int x1 = p1 >= 0 ? num1.charAt(p1) - '0' : 0;
            int x2 = p2 >= 0 ? num2.charAt(p2) - '0' : 0;
            int value = (x1 + x2 + carry) % 10;
            carry = (x1 + x2 + carry) / 10;
            res.append(value);
            p1--;
            p2--; 
        }
        
        if (carry != 0)
            res.append(carry);
        
        return res.reverse().toString();
    }
```
