#222. Count Complete Tree Nodes 

```
Given a complete binary tree, count the number of nodes.

Definition of a complete binary tree from Wikipedia:
In a complete binary tree every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.

Subscribe to see which companies asked this question
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
    public int countNodes(TreeNode root) {
        if(root==null) return 0;
        int left = getHeight(root, true);
        int right = getHeight(root,false);
        if(left == right) return (1<<left)-1;
        else return countNodes(root.left)+countNodes(root.right)+1;
        
        
    }
    
    public int getHeight(TreeNode root, boolean tag)
    {
        int h =0;
        while(root!=null)
        {
            if(tag) root = root.left;
            else root =root.right;
            h++;
        }
        
        return h;
    }
}
```
