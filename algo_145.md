#145. Binary Tree Postorder Traversal 
```
Given a binary tree, return the postorder traversal of its nodes' values.

For example:
Given binary tree {1,#,2,3},
   1
    \
     2
    /
   3
return [3,2,1].
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
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<Integer>();
        Stack<TreeNode> stack = new Stack<TreeNode>();
        if(root==null) return res;
        stack.push(root);
        while(!stack.isEmpty())
        {
            TreeNode cur = stack.pop();
            res.add(cur.val);
            if(cur.right!=null) stack.push(cur.right);
            if(cur.left!=null) stack.push(cur.left);
        }
        return res;
    }
}

```


```java
public class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<Integer>();
        if(root!=null) preorderHelper(root,res);
        return res;
    }
    private void preorderHelper(TreeNode root, List<Integer> res)
    {
        res.add(root.val);
        if(root.left!=null) preorderHelper(root.left,res);
        if(root.right!=null) preorderHelper(root.right,res);
    }
}

```
