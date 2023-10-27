### Maximum Gap
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

##### Example 1
- Input: nums = [3,6,9,1]
- Output: 3
- Explanation: The sorted form of the array is [1,3,6,9], either (3,6) or (6,9) has the maximum difference 3.
    
##### Example 2
- Input: nums = [10]
- Output: 0
- Explanation: The array contains less than 2 elements, therefore return 0.

##### Example 3
- Input: nums = [12]
- Output: 1
- Explanation: The array contains less than 3 elements, therefore return 1.

```javascript
<!-- correct_solution -->
var maximumGap = function(nums) {
//This method will be called to match the expected result
//So write a well tested and correct code
}
```
```javascript
<!-- runOneTestCaseHandler -->
var runOneTestCaseHandler(nums, target) {
    var result = maximumGap(nums, target);
    var expectedResult = maximumGap_solution(nums, targets) ;
    if(expectedResult !== result) {
        throw new Error('Test case failed for input : nums = ' + nums + ' target = ' + targets);
    }
    return true ;
}

var nums = <param1Value> ;
var target = <param2Value> ;
var result = runOneTestCaseHandler(nums, target);
console.log('Test case passed : ' + result) ;
```
```javascript
<!-- runAllTestCases -->
var runAllTestCases() {
    const totalTestCases = 3 ;
    const nums = [[2, 7, 11, 15],[3, 2, 4],[3, 3]];
    const targets = [9, 6, 6];
    
    for(const i = 0 ; i < totalTestCases.length ; i++) {
        var result = maximumGap(nums, target);
        var expectedResult = maximumGap_solution(nums, targets) ;
        if(expectedResult !== result) {
            throw new Error('Test case failed for input : nums = ' + nums[i] + ' target = ' + targets[i]);
        }
    }
    return true ;
}
var result = runAllTestCases();
console.log('All test cases passed : ' + result) ;
```

##### Constraints:
- 1 <= nums.length <= 105
- 0 <= nums[i] <= 109
