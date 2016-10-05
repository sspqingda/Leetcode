#230. Kth Smallest Element in a BST
```
Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.

Note: 
You may assume k is always valid, 1 ≤ k ≤ BST's total elements.

Follow up:
What if the BST is modified (insert/delete operations) often and you need to find the kth smallest frequently? How would you optimize the kthSmallest routine?
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
    public int kthSmallest(TreeNode root, int k) {
        int count = 0;
        int res = 0;
        Stack<TreeNode> stack = new Stack<TreeNode>();
        TreeNode cur = root;
        while(!stack.isEmpty()||cur!=null)
        {
            if(cur!=null)
            {
                stack.push(cur);
                cur =cur.left;
            }
            
            else if(!stack.isEmpty())
            {
                cur = stack.pop();
                count++;
                if(count==k) res = cur.val;
                cur = cur.right;
                
            }
        }
        return res;
        
    }
}

```


```java
public class Solution {
    public int kthSmallest(TreeNode root, int k) {
        int val = 0;
        int count = treeSize(root.left) +1;
        if(count==k)  val = root.val;
        else if(count>k) 
        {
            val = kthSmallest(root.left,k);
        }
        else if(count<k)
        {
            val = kthSmallest(root.right,k-count);
        }
        return val;
    }
    private int treeSize(TreeNode root)
    {
        if(root ==null) return 0;
        return treeSize(root.left)+treeSize(root.right)+1;
      
    }
}
```
