# Longest Common Prefix

This algorithm finds the longest common prefix among a set of strings. It starts by sorting the array of strings (`strs`), then initializes a `StringBuilder` to build the common prefix. The first and last strings in the sorted array are compared, as any common prefix between all strings must also be a prefix of these two strings. The algorithm iterates through the characters of the first string, comparing each character with the corresponding character in the last string. If they match, the character is added to the `commonPrefix`; if they don't match or the comparison exceeds the length of the last string, the algorithm returns the `commonPrefix` found so far. If the first and last strings are identical, the entire string is returned as the common prefix.

### Code complexity
Time complexity **O(n log(n))** Due to the avarage time of the sort algorithm `Arrays.sort(strs)`\
Space complexity: **O(n)** There is a `StringBuilder` that increases every char appended in the object.

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args) {
        var solution = new Solution();
        System.out.println(solution.longestCommonPrefix(new String[] {"flower","flow","flight"})); // "fl"
        System.out.println(solution.longestCommonPrefix(new String[] {"ab","a"})); // "a"
        System.out.println(solution.longestCommonPrefix(new String[] {"dog","racecar","car"})); // ""
    }

    public boolean isSubsequence(String s, String t) {
        Arrays.sort(strs);
        StringBuilder commonPrefix = new StringBuilder();
        String first = strs[0];
        String last = strs[strs.length - 1];

        if (first.equals(last)) {
            return first;
        }

        for (int i = 0; i < first.length(); i++) {
            char letter = first.charAt(i);
            if (i + 1 > last.length() || last.charAt(i) != letter) {
                return commonPrefix.toString();
            }
            commonPrefix.append(letter);
        }
        return commonPrefix.toString();
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/longest-common-prefix/)
