# 3 Sum challenge

This algorithm uses the same strategy for the [Two Sum 2](https://github.com/Murillo/Leetcode-Challenges/blob/main/algorithms/TwoSum2.md). In this challenge, there are two loops. The first loop defines the target, while the second loop gets the Two Sum. For a combination to be stored, the sum of the target and Two Sum must be zero. If the sum is not zero, the procedure checks whether it is greater or smaller than zero, and moves the left or right pointers accordingly.  

### Code complexity
Time complexity **O(n^2)** This is N squared due to the first loop to define the target and the second one to define the two sum\
Space complexity: **O(n)** Due to the sort algorithm and the collection to store the three sums combination.

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args) {
        Solution solution = new Solution();
        var result1 = solution.threeSum(new int[] { -1,0,1,2,-1,-4 });
    }

    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> sums = new ArrayList<>();
        Arrays.sort(nums);
        if (nums[0] > 0){
            return sums;
        }

        for (int i = 0; i < nums.length - 1; i++) {
            int target = nums[i];
            if (i > 0 && target == nums[i - 1]){
                continue;
            }

            int left = i + 1;
            int right = nums.length - 1;
            while (left < right) {
                if (nums[right] + nums[left] + target == 0) {
                    sums.add(Arrays.asList(target, nums[left], nums[right]));
                }

                if ((target + nums[right] + nums[left]) > 0) {
                    right -= 1;
                    while (right > left && nums[right] == nums[right + 1]){
                        right -= 1;
                    }
                } else {
                    left += 1;
                    while (left < right && nums[left] == nums[left - 1]){
                        left += 1;
                    }
                }
            }
        }
        return sums;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/3sum/)
