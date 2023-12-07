# Same Tree

Algorithm designed to determine tree depth using stacks instead of recursion. The function checks for parity between the left and right nodes.

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
import java.util.ArrayList;

public class Solution {

    public static void main(String[] args){
        //        1
        //    2       5
        //               8
        TreeNode node1 = new TreeNode(1, new TreeNode(2), new TreeNode(5, null, new TreeNode(8)));
        TreeNode node2 = new TreeNode(1, new TreeNode(2), new TreeNode(5, null, new TreeNode(8)));
        TreeNode node3 = new TreeNode(1, new TreeNode(2), new TreeNode(5, null, new TreeNode(9)));
        Solution solution = new Solution();
        System.out.println(solution.isSameTree(node1, node2)); // Output: True
        System.out.println(solution.isSameTree(node1, node3)); // Output: False
    }

    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) {
            return true;
        }
        if (isDifferent(p, q)){
            return false;
        }
        var nodeListP = new ArrayList<TreeNode>();
        nodeListP.add(p.left);
        nodeListP.add(p.right);

        var nodeListQ = new ArrayList<TreeNode>();
        nodeListQ.add(q.left);
        nodeListQ.add(q.right);

        while (!nodeListP.isEmpty() || !nodeListQ.isEmpty()){
            TreeNode nodeP = nodeListP.remove(nodeListP.size()-1);
            TreeNode nodeQ = nodeListQ.remove(nodeListQ.size()-1);
            if (nodeP == null && nodeQ == null) {
                continue;
            }
            if (isDifferent(nodeP, nodeQ)){
                return false;
            }
            nodeListP.add(nodeP.left);
            nodeListP.add(nodeP.right);
            nodeListQ.add(nodeQ.left);
            nodeListQ.add(nodeQ.right);
        }
        return true;
    }

    private boolean isDifferent(TreeNode p, TreeNode q) {
        if ((p != null && q == null) || (p == null && q != null)) {
            return true;
        }
        if (p.val != q.val){
            return true;
        }
        return false;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
