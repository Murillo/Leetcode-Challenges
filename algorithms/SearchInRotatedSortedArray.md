# Search in Rotated Sorted Array

It is applied Two Pointers to store the left and right indices to search a rotated, ordered array for a target value.

### Code complexity
Time complexity **O(log n)** Each iteration, the n is reduced by half\
Space complexity: **O(1)** There are only 3 variables, that is the amount and size of variables are constant.

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.search(new int[]{4,5,6,7,0,1,2}, 0)); // 4
        System.out.println(solution.search(new int[]{4,5,6,7,0,1,2}, 3)); // -1
        System.out.println(solution.search(new int[]{1}, 0)); // -1
    }

    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;

        while (left <= right){
            if (nums[left] == target){
                return left;
            }
            if (nums[right] == target) {
                return right;
            }

            int mid = (left + right) / 2;
            if (nums[mid] == target) {
                return mid;
            }

            if (nums[left] < nums[mid]) {
                if (nums[left] <= target && target <= nums[mid] ) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            } else {
                if (nums[right] >= target && target >= nums[mid] ) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }
        return -1;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/search-in-rotated-sorted-array/)
