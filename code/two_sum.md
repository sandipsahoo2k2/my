## Two Sum
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.

#### Example 1:
- Input: nums = [2,7,11,15], target = 9
- Output: [0,1]
- Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
  
#### Example 2:
- Input: nums = [3,2,4], target = 6
- Output: [1,2]

#### Example 3:
- Input: nums = [3,3], target = 6
- Output: [0,1]

#### Constraints:
- 2 <= nums.length <= 104
- -109 <= nums[i] <= 109
- -109 <= target <= 109
  
Only one valid answer exists.

```javascript
<!-- question -->
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    
};
```
```javascript
<!-- correct_solution -->
var twoSum = function(nums, target) {
    
};
```
```javascript
<!-- runOneTestCaseHandler -->
var runOneTestCaseHandler(args) {
    return twoSum(...args) ;
}
var result = runOneTestCaseHandler(inputArgs);
console.log('Test case returned : ' + result) ;
```
```javascript
<!-- runAllTestCases -->
var runAllTestCases() {
    const totalTestCases = 3 ;
    const nums = [[2, 7, 11, 15],[3, 2, 4],[3, 3]];
    const targets = [9, 6, 6];
    const expectedResults = [3,0,1] ;
    
    for(const i = 0 ; i < totalTestCases.length ; i++) {
        var result = twoSum(nums, target);
        if(expectedResults[i] !== result) {
            throw new Error('Test case failed for input : nums = ' + nums[i] + ' target = ' + targets[i]);
        }
    }
    return true ;
}
var result = runAllTestCases();
console.log('All test cases passed : ' + result) ;
```

Expectations: Solve the problem in Log(N) Time 
