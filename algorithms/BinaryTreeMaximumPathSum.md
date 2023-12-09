# Binary Tree Maximum Path Sum

Algorithm to sum the max path of the sum using DFS.

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
        //    2      5
        //  3   4      8
        TreeNode node = new TreeNode(1, new TreeNode(2, new TreeNode(3), new TreeNode(4)), new TreeNode(5, null, new TreeNode(8)));
        Solution solution = new Solution();
        System.out.println(solution.maxPathSum(node));
    }

    private int maxPath = 0;
    public int maxPathSum(TreeNode root) {
        this.maxPath = root.val;
        this.maxPathSumDFS(root);
        return this.maxPath;
    }

    private int maxPathSumDFS(TreeNode root) {
        if (root == null) {
            return 0;
        }
        int left = maxPathSumDFS(root.left);
        int right = maxPathSumDFS(root.right);
        left = Math.max(left, 0);
        right = Math.max(right, 0);
        this.maxPath = Math.max(this.maxPath, left + right + root.val);
        return root.val + Math.max(left, right);
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/binary-tree-maximum-path-sum/)
