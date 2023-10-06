# Container With Most Water

To find the maximum area between the values of a collection, this solution uses the Two Pointers algorithm. Since the biggest area would be between the extreme points of the collection, we move the pointers towards the center of the collection. Then, we multiply the minimum height with the distance between the pointers to get the maximum area.

### Code complexity
Time complexity **O(n)** The algorithm processes the entire collection in a single run.\
Space complexity: **O(1)** There are only some variables storing primitive values in the memory stack.

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args) {
        Solution solution = new Solution();
        System.out.println(solution.maxArea(new int[]{1,8,6,2,5,4,8,3,7})); // Output: 49
    }

    public int maxArea(int[] height) {
        int maxArea = 0;
        int left = 0;
        int right = height.length - 1;
        while (left < right){
            int minHeight = height[left] > height[right] ? height[right] : height[left];
            int maxAreaTemp = minHeight * (right - left);
            if (maxAreaTemp > maxArea){
                maxArea = maxAreaTemp;
            }
            if (height[left] > height[right]) {
                right -= 1;
            }else{
                left += 1;
            }
        }
        return maxArea;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/container-with-most-water/)
