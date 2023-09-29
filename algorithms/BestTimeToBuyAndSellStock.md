# Best Time to Buy and Sell Stock

In this method, the collection received will be iterated to find the largest difference between the numbers. The method will use two constant variables, namely max (to store the largest difference) and min (to store the smallest number at the current iteration). The difference between the numbers will be checked at each iteration. 

### Code complexity
Time complexity **O(n)** The method will iterate the received collection once via `for`\
Space complexity: **O(1)** Ignoring the collection received as parameter, the method will store only two variables.

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.maxProfit(new int[]{7,1,5,3,6,4})); // Output: 5
        System.out.println(solution.maxProfit(new int[]{7,6,4,3,1})); // Output: 0
        System.out.println(solution.maxProfit(new int[]{7,6,10,5,7,12})); // Output: 7
    }
    
    public int maxProfit(int[] prices) {
        int min = prices[0];
        int max = 0;
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] < min) {
                min = prices[i];
                continue;
            }
    
            if (prices[i] - min > max) {
                max = prices[i] - min;
            }
        }
        return max;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
