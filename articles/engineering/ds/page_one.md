## Why page one ?
Sometimes what looks simple is hard in an interview environment, so I thought adding few important basics that may be helpful should I add here.

1. If your preferred language to code is java ( not python ) then you need to know few basics dealing with arrays.
   
* 

Here is a simple program to do batch processing for a job. This is actually a very practical problem that we build time to time.

Write a method to count number of inputs in each bucket that you create according to their face value.
So e.g If given facevalue of an input is 53 with bucket_size = 10 then it will go to the 6th bucket and any 
input which can't be mapped to a bucket will go to the last bucket. Here is the solution to this problem.

```
public static void batch(int[] inputs, int totalBuckets, int bucket_size) {
        Map<Integer, List<Integer>> map = new HashMap<>() ;
        for(int l : latency) {
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
