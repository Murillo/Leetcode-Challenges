# Number of 1 Bits

An integer is represented by a set of bits, which can be either 0 or 1. For example, the integer 9 is represented as 1001, with two ones. In this challenge, we will use the right shift operator to reduce the number of bits during each iteration. We will also use the & operator to check if the first bit is 1. If the first bit is indeed 1, the function will add one to the counter and continue with the right shift operator.

### Code complexity
Time complexity **O(log n)**\
Space complexity: **O(1)**

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args){
        Solution solution = new Solution();
        System.out.println(solution.hammingWeight(5)); // Output: 2
    }

    public int hammingWeight(int n) {
        int count = 0;
        while (n != 0) {
            if ((n & 1) == 1) {
                count++;
            }
            n >>= 1;
        }
        return count;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/number-of-1-bits/)
