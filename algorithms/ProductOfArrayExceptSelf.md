# Product of Array Except Self

There are many ways to resolve this challenge. However, the Leetcode requested to not use the division operator.

In order to solve the problem, it is necessary to split the product calculation into two stages by utilizing the prefixSum technique. This technique involves applying a mathematical operation, such as sum, or subtraction the current indicator with the previous one, and storing the result. This value is then accumulated with each new iteration.

In this specific case, the first loop stores the value of product 1 in the first index, and applies the calculation to obtain the product in the subsequent indexes. Once the first loop has ended, a second loop is initialized, starting at the end of the collection, and applies the same operation until it reaches index 0.

### Code complexity
Time complexity **O(n)** There are 2 `for`, but they will iterate the `nums` collection once separated. \
Space complexity: **O(n)** A new collection is created with same `nums` size to store the products.

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println("---- Test 1 ---");
        var products = solution.productExceptSelf(new int[]{1,2,3,4}); // [24,12,8,6]
        for (int item : products){
            System.out.println(item);
        }

        System.out.println("---- Test 2 ---");
        var products2 = solution.productExceptSelf(new int[]{-1,1,0,-3,3}); // [0,0,9,0,0]
        for (int item : products2){
            System.out.println(item);
        }
    }

    public int[] productExceptSelf(int[] nums) {
        int nextProduct = 1;
        int[] products = new int[nums.length];
        for(int i = 0; i < nums.length; i++) {
            products[i] = nextProduct;
            nextProduct = nextProduct * nums[i];
        }

        nextProduct = 1;
        for(int i = nums.length - 1; i >= 0; i--) {
            products[i] = products[i] * nextProduct;
            nextProduct = nextProduct * nums[i];
        }
        return products;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/product-of-array-except-self)
