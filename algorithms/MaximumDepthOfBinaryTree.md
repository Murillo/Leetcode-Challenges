# Maximum Depth of Binary Tree

When searching for the greatest depth in a tree, a recursive function is used that traverses all nodes using Depth-first search.

### Code complexity
Time complexity **O(n)** \
Space complexity: **O(n)**

### Java implementation

``` Java
public class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(){}
    TreeNode(int val) {
        this.val = val;
    }
    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

```

``` Java
public class Solution {

    public static void main(String[] args){
        //        1
        //    2       5
        //               8
        TreeNode node = new TreeNode(1, new TreeNode(2), new TreeNode(5, null, new TreeNode(8)));
        Solution solution = new Solution();
        System.out.println(solution.maxDepth(node)); // Output: 3
    }

    public int maxDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        return Math.max(maxDepthRecursive(root.left, 2), maxDepthRecursive(root.right, 2));
    }

    private int maxDepthRecursive(TreeNode root, int depth) {
        if (root == null) {
            return depth - 1;
        }
        int left = maxDepthRecursive(root.left, depth + 1);
        int right = maxDepthRecursive(root.right, depth + 1);
        return Math.max(left, right);
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
