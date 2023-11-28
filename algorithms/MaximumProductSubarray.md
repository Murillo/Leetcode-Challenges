# Maximum Product Subarray

In order to solve this problem, it is necessary to store the product in two variables, one to contain the maximum and the other to contain the minimum. This is because when multiplying numbers, a negative number will result in a negative value, which is the minimum. However, if another negative value is included in the calculation, the result will be positive. To handle this, two variables are used to store the maximum and minimum values during iteration.

### Code complexity
Time complexity **O(n)** Each iteration, the maximum product subarray is calculated\
Space complexity: **O(1)** There are a few variables with constant size.

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.maxProduct(new int[] {2,3,-2,4} )); // Output: 6
        System.out.println(solution.maxProduct(new int[] {-2,0,-1} )); // Output: 0
    }
    public int maxProduct(int[] nums) {
        if (nums.length == 0){
            return 0;
        }
        int max = nums[0];
        int prev_min = nums[0];
        int prev_max = nums[0];
        int current_min = nums[0];
        int current_max = nums[0];

        for (int i = 1; i < nums.length; i++) {
            current_max = Math.max(Math.max(prev_max * nums[i], prev_min * nums[i]), nums[i]);
            current_min = Math.min(Math.min(prev_max * nums[i], prev_min * nums[i]), nums[i]);
            max = Math.max(current_max, max);
            prev_max = current_max;
            prev_min = current_min;
        }
        return max;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/maximum-product-subarray/)
