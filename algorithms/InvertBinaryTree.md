# Invert Binary Tree

Algorithm to invert a tree using recursion.

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
class Solution {

    public static void main(String[] args){
        //        1
        //    2      5
        //  3   4      8
        TreeNode node = new TreeNode(1, new TreeNode(2, new TreeNode(3), new TreeNode(4)), new TreeNode(5, null, new TreeNode(8)));
        Solution solution = new Solution();
        var result = solution.invertTree(node);
    }

    public TreeNode invertTree(TreeNode root) {
        if (root == null) {
            return null;
        }

        TreeNode leftTemp = root.left;
        root.left = root.right;
        root.right = leftTemp;
        if (root.left != null){
            invertTree(root.left);
        }
        if (root.right != null) {
            invertTree(root.right);
        }
        return root;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/invert-binary-tree/)
