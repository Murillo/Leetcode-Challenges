# Rotate Array

The solution to this challenge involves using 3 for loops. The first loop is used to reverse the entire array, the second to reverse only the initial rotated section, and the third to reverse the remainder of the array.

### Code complexity
Time complexity **O(n)** \
Space complexity: **O(1)** No additional array is created

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args) {
        var solution = new Solution();
        solution.rotate(new int[] { 1, 2, 3, 4, 5, 6, 7 }, 3);
    }

    public void rotate(int[] nums, int k) {
        k = k % nums.length;
        if (k == 0) {
            return;
        }

        for (int i = 0; i < (nums.length / 2); i++) {
            int tempLast = nums[(nums.length - 1) - i];
            int tempFirst = nums[i];
            nums[i] = tempLast;
            nums[(nums.length - 1) - i] = tempFirst;
        }

        for  (int i = 0; i < (k / 2); i++) {
            int tempLast = nums[(k - 1) - i];
            int tempFirst = nums[i];
            nums[i] = tempLast;
            nums[(k - 1) - i] = tempFirst;
        }

        int endIndexControl = 0;
        int total = k + ((nums.length - k) / 2);
        for  (int i = k; i < total; i++) {
            int tempLast = nums[(nums.length - 1) - endIndexControl];
            int tempFirst = nums[i];
            nums[i] = tempLast;
            nums[(nums.length - 1) - endIndexControl] = tempFirst;
            endIndexControl += 1;
        }
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/rotate-array/)
