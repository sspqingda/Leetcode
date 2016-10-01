#94. Binary Tree Inorder Traversal 

```
Given a binary tree, return the inorder traversal of its nodes' values.

For example:
Given binary tree [1,null,2,3],
   1
    \
     2
    /
   3
return [1,3,2].

Note: Recursive solution is trivial, could you do it iteratively?
```

``` java
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
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<Integer>();
       
        if(root!=null) inorderHelper(root,res);
        return res;
    }
    
    private void inorderHelper(TreeNode root, List<Integer> res)
    {
        if(root.left != null) inorderHelper(root.left,res);
        res.add(root.val);
        if(root.right!=null) inorderHelper(root.right,res);
    }
}
```

```java

//Moris Inorder
public class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<Integer>();
        TreeNode cur = root;
        while(cur !=null)
        {
            if(cur.left !=null)
            {
                TreeNode pre = cur.left;
                while(pre.right!=null && pre.right !=cur)
                {
                    pre = pre.right;
                }
                if(pre.right ==null)
                {
                    pre.right = cur;
                    cur = cur.left;
                }
                else if(pre.right ==cur)
                {
                    pre.right =null;
                    res.add(cur.val);
                    cur = cur.right;
                }
            }
            else
            {
                res.add(cur.val);
                cur = cur.right;
            }
            
        }
        
        return res;
     
    }
}

```

```java

public class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<Integer>();
        Stack<TreeNode> stack = new Stack<TreeNode>();
        if(root == null) return res;
        while(root!=null ||!stack.isEmpty())
        {
            if(root!=null)
            {
                stack.push(root);
                root = root.left;
            }
            else if(!stack.isEmpty())
            {
                root = stack.pop();
                res.add(root.val);
                root = root.right;
            }
        }
        
        return res;
    }
}

```
