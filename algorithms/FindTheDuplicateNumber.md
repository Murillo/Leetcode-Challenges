# Find the Duplicate Number

The code challenge uses the "Floyd's Tortoise and Hare Algorithm", using a cycle where two pointers traverse the array received to find the duplicated number.

The time complexity of the code is O(n), where n is the size of the input array. This is because the algorithm traverses the array only once to find the duplicate number. The space complexity is O(1), as the algorithm only uses two additional variables to track the indices in the array.

### Code complexity
Time complexity **O(n)** \
Space complexity: **O(1)**

### Java implementation

``` Java
package findtheduplicatenumber;

public class Solution {
    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.findDuplicate(new int[]{1,3,4,2,2})); //2
    }

    public int findDuplicate(int[] nums) {
       int slow = nums[nums[0]];
       int fast = nums[nums[nums[0]]];
       while (slow != fast) {
           slow = nums[slow];
           fast = nums[nums[fast]];
       }

       slow = nums[0];
       while (slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
       }
        return slow;
    }
}

```

### References
[Leetcode](https://leetcode.com/problems/find-the-duplicate-number/)
