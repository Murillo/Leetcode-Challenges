# Best Time to Buy and Sell Stock II

The implementation is similar to [Best Time to Buy and Sell Stock I](https://github.com/Murillo/Leetcode-Challenges/blob/main/algorithms/BestTimeToBuyAndSellStock.md). The challenge involves adding up all differences to calculate total profit, instead of finding the largest difference.

### Code complexity
Time complexity **O(n)** The method will iterate the received collection once via `for`\
Space complexity: **O(1)** Ignoring the collection received as parameter, the method will store only two variables.

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.maxProfit(new int[]{7,1,5,3,6,4})); // Output: 7
        System.out.println(solution.maxProfit(new int[]{1,2,3,4,5})); // Output: 4
        System.out.println(solution.maxProfit(new int[]{7,6,4,3,1})); // Output: 0
    }

    public int maxProfit(int[] prices) {
        int min = prices[0];
        int max = 0;
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] < prices[i - 1]) {
                max += (prices[i - 1] - min);
                min = prices[i];
            }
        }
        if (prices[prices.length-1] > min) {
            max += (prices[prices.length-1] - min);
        }
        return max;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)
