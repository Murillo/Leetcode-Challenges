# Two Sum challenge

To prevent iterating over the number collection multiple times, a ***Hashmap*** is created to store the difference between target and each previously encountered number. In the next iteration, the code checks if the current number is the remaining value of any subtraction performed previously. This approach helps to optimize the code's performance and avoid unnecessary computations.

### Code complexity
Time complexity **O(n)**\
Space complexity: **O(n)**

### Java implementation

``` Java
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> subtractsMap = new HashMap<Integer, Integer>();
        int firstNumber = 0;
        int secondNumber = 0;
        for (int i = 0; i < nums.length; i++) {
            if (subtractsMap.containsKey(nums[i])) {
                firstNumber = subtractsMap.get(nums[i]);
                secondNumber = i;
                break;
            }
            subtractsMap.put(target - nums[i], i);
        }
        return new int[] { firstNumber, secondNumber};
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/two-sum/)
