# Climbing Stairs
This is a dynamic programming challenge that can be solved in two ways: top-down and bottom-up. In the top-down algorithm, a recursive function is used to search for all possible combinations. At each step, there are two options: climb the next step or climb two steps. The recursive function checks all possibilities based on this condition. To save time and algorithm resources, the memoization technique is used to avoid repetition of values. In the bottom-up algorithm, there is no use of a recursive function since the approach is to start with the last step.

## Top down
### Code complexity
Time complexity **O(n)**\
Space complexity: **O(n)**

### Java implementation

``` Java
import java.util.HashMap;
import java.util.Map;

public class Solution {

    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.climbStairs(1)); // Output: 1
        System.out.println(solution.climbStairs(2)); // Output: 2
        System.out.println(solution.climbStairs(3)); // Output: 3
        System.out.println(solution.climbStairs(5)); // Output: 8
    }

    public int climbStairs(int n) {
        Map memoization = new HashMap<Integer, Integer>();
        return this.climbRecursive(1, n, memoization) + this.climbRecursive(2, n, memoization);
    }

    private int climbRecursive(int i, int target, Map<Integer, Integer> memoization) {
        if (memoization.containsKey(i)) {
            return memoization.get(i);
        }
        if (i == target) {
            return 1;
        }
        if (i > target) {
            return 0;
        }
        int total = this.climbRecursive(i + 1, target, memoization) + this.climbRecursive(i + 2, target, memoization);
        memoization.putIfAbsent(i, total);
        return total;
    }
}

```

## Bottom up
### Code complexity
Time complexity **O(n)**\
Space complexity: **O(n)**

### Java implementation

``` Java
public class Solution {

    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.climbStairs(1)); // Output: 1
        System.out.println(solution.climbStairs(2)); // Output: 2
        System.out.println(solution.climbStairs(3)); // Output: 3
        System.out.println(solution.climbStairs(5)); // Output: 8
    }

    public int climbStairs(int n) {
        int lastStep = 1;
        int prevStep = 1;
        for (int i = n - 2; i >= 0; i--) {
            int curr = prevStep + lastStep;
            lastStep = prevStep;
            prevStep = curr;
        }
        return prevStep;
    }
}

```

### References
[Leetcode](https://leetcode.com/problems/climbing-stairs)
