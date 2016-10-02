#124. Binary Tree Maximum Path Sum  QuestionEditorial Solution  My Submissions
```
Given a binary tree, find the maximum path sum.

For this problem, a path is defined as any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The path does not need to go through the root.

For example:
Given the below binary tree,

       1
      / \
     2   3
Return 6.
```


```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public int maxPathSum(TreeNode root) {
        int[] res = new int[1];
        res[0] = Integer.MIN_VALUE;
        maxPath(root,res);
        return res[0];
        
    }
    
    private int maxPath(TreeNode root, int[] res)
    {
        if(root ==null) return 0;
        int left = maxPath(root.left,res);
        int right = maxPath(root.right,res);
        int single = Math.max(root.val,Math.max(left,right)+root.val);
        int arc = left+right+root.val;
        res[0] = Math.max(res[0],Math.max(arc,single));
        return single;
        
    }
}
```
