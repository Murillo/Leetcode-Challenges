# Maximum Subarray

When we talk about a subarray, it can be any contiguous sequence within an array, which can be as small as a single element or can include all the elements. The Sliding Window algorithm is used to traverse the entire collection and determine the largest subarray. The larger the subarray, the higher the probability of having the largest sum. However, the presence of negative values in the array can have a negative impact on the count. To address this, every time we encounter a negative number, we reset the count to zero.

### Code complexity
Time complexity **O(n)** as the function traverses the array only once, it is efficient and does not need to repeat the process.\
Space complexity: **O(1)** it only stores two variables with the maximum sequence.

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.maxSubArray(new int[] {-2,1,-3,4,-1,2,1,-5,4} )); // Output: 6
    }
    public int maxSubArray(int[] nums) {
        int max = nums[0];
        int maxSeq = nums[0];
        for (int i = 1; i < nums.length; i++) {
            if (maxSeq < 0) {
                maxSeq = 0;
            }
            maxSeq += nums[i];
            max = Math.max(maxSeq, max);
        }
        return max;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/maximum-subarray)
