# Kadane Algorithm
**Kadane's Algorithm** an efficient program to find the [[sum of contiguous subarray]] within one-dimensional array of numbers that has largest sum.

``` java
class Solution {
    public int maxSubArray(int[] nums) {
        int max = nums[0];
        int maxEnd = nums[0];
        for(int i=1; i<nums.length; i++){
            maxEnd = Math.max(maxEnd + nums[i], nums[i]);
            max = Math.max(max, maxEnd);
        }
        return max;
    }
}
```
