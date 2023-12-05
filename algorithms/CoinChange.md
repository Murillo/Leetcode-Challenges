# Coin Change
Dynamic Programming solution using a bottom-up approach.

## Bottom up solution
### Code complexity
Time complexity **O(amount * coins)**\
Space complexity: **O(amount)**

### Java implementation

``` Java
import java.util.Arrays;

public class Solution {
    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.coinChange(new int[] { 1,2,5 }, 11)); // Output: 3
        System.out.println(solution.coinChange(new int[] { 2 }, 3)); // Output: -1
        System.out.println(solution.coinChange(new int[] { 1 }, 0)); // Output: 0
    }

    public int coinChange(int[] coins, int amount) {
        int[] solutions = new int[amount + 1];
        Arrays.fill(solutions, amount + 1);
        solutions[0] = 0;
        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (i - coin >= 0) {
                    solutions[i] = Math.min(solutions[i], 1 + solutions[i - coin]);
                }
            }
        }
        return solutions[amount] != amount + 1 ? solutions[amount] : -1;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/coin-change)
