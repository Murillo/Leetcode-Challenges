# Invert Binary Tree

This algorithm involves checking every character in a variable called `t`. A new variable `cursor` is created to store the position being checked in variable `s`. Each time the characters match, the `cursor` increments by 1. If the cursor value is the same as the value of variable `s`, it indicates that `s` is a sub-sequence of `t`.

### Code complexity
Time complexity **O(n)** In the worst-case scenario, the method will iterate through all the characters of variable `t` to check if `s` is a subsequence.\
Space complexity: **O(1)** Only one variable was created to store the position of the char in the string `s`

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args) {
        var solution = new Solution();
        System.out.println(solution.isSubsequence("abc", "ahbgdc")); // true
        System.out.println(solution.isSubsequence("axc", "ahbgdc")); // false
        System.out.println(solution.isSubsequence("a", "a")); // true
        System.out.println(solution.isSubsequence("ab", "b")); // false
        System.out.println(solution.isSubsequence("", "abcdef")); // true
    }

    public boolean isSubsequence(String s, String t) {
        if ((s.length() == t.length() && s.equals(t)) || s.equals("")) {
            return true;
        }
        int cursor = 0;
        for (int i = 0; i < t.length(); i++) {
            if (t.charAt(i) == s.charAt(cursor)) {
                cursor += 1;
                if (cursor == s.length()) {
                    return true;
                }
            }
        }
        return false;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/is-subsequence/)
