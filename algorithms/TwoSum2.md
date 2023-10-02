#  Two Sum II - Input Array Is Sorted

This technique uses two pointers to traverse the sorted list at once and find the pair of numbers that add up to the given target.

### Code complexity
Time complexity **O(n)**\
Space complexity: **O(1)**

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args) {
        Solution solution = new Solution();
        int[] result = solution.twoSum(new int[] { 1, 2, 4, 9, 10, 20}, 13); // Output = [3,4]
        System.out.println(String.join(",", Arrays.stream(result)
                .mapToObj(Integer::toString)
                .toArray(String[]::new)));
    }

    public int[] twoSum(int[] numbers, int target) {
        int left = 0;
        int right = numbers.length - 1;
        while (left < right) {
            if ((numbers[right] + numbers[left]) == target) {
                return  new int[] { left + 1, right + 1};
            }

            if ((numbers[right] + numbers[left]) > target) {
                right -= 1;
            } else {
                left += 1;
            }
        }
        return new int[] {};
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted)
