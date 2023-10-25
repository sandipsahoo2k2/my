## Maximum Gap
Given an integer array nums, return the maximum difference between two successive elements in it's sorted form.
If the array contains less than two elements, return 0.
You must write an algorithm that runs in linear time and uses linear extra space.

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var maximumGap = function(nums) {
    
};
```

<dl>
  <dt>Example 1</dt>
      <dd>Input: nums = [3,6,9,1]</dd>
      <dd>Output: 3</dd>
      <dd>Explanation: The sorted form of the array is [1,3,6,9], either (3,6) or (6,9) has the maximum difference 3.</dd>
  <dt>Example 2</dt>
      <dd>Input: nums = [10]</dd>
      <dd>Output: 0</dd>
      <dd>Explanation: The array contains less than 2 elements, therefore return 0.</dd>
</dl>

#### Test Cases
1. Example 1
   - Input: nums = [3,6,9,1]
   - Output: 3
   - Explanation: The sorted form of the array is [1,3,6,9], either (3,6) or (6,9) has the maximum difference 3.
      
2. Example 2
   - Input: nums = [10]
   - Output: 0
   - Explanation: The array contains less than 2 elements, therefore return 0.

#### Constraints:
- 1 <= nums.length <= 105
- 0 <= nums[i] <= 109
