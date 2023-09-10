# Contains Duplicate challenge

To avoid using a brute force algorithm with a time complexity 
of O(n^2), it is created a solution that uses the ***Set*** data structure. 
The Set only allows unique value that is also the key, so if 
there are any duplicates in the collection, 
the data structure will indicate it, and this algorithm 
will return True. This method is more efficient than 
the brute force algorithm.

### Code complexity
Time complexity **O(n)**\
Space complexity: **O(n)**

### Java implementation
``` Java
public class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> numsSet = new HashSet<>();
        for (int num : nums) {
            if (numsSet.contains(num)){
                return true;
            }
            numsSet.add(num);
        }
        return false;
    }
}
```
### References
[Leetcode](https://leetcode.com/problems/contains-duplicate/)
