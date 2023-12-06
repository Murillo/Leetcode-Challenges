# Longest Increasing Subsequence

Dynamic programming using the Bottom-up technique.

### Code complexity
Time complexity **O(n^2)**\
Space complexity: **O(n)**

### Java implementation
``` Java
import java.util.Arrays;

class Solution {

    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.lengthOfLIS(new int[] { 0,1,0,3,2,3 })); // Output: 4
        System.out.println(solution.lengthOfLIS(new int[] { 10,9,2,5,3,7,101,18 })); // Output: 4
        System.out.println(solution.lengthOfLIS(new int[] { 7,7,7,7,7,7,7 })); // Output: 1
    }
    public int lengthOfLIS(int[] nums) {
        int[] solutions = new int[nums.length];
        Arrays.fill(solutions, 1);
        int longestSubsequence = 1;
        for (int i = 1; i < nums.length; i++) {
            for (int j = 0; j < nums.length; j++) {
                if (j == i) {
                    break;
                }
                if (nums[j] < nums[i]) {
                    solutions[i] = Math.max(solutions[j] + 1, solutions[i]);
                    longestSubsequence = Math.max(longestSubsequence, solutions[i]);
                }
            }
        }
        return longestSubsequence;
    }
}
```
### References
[Leetcode](https://leetcode.com/problems/longest-increasing-subsequence)
