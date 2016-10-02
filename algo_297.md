#297. Serialize and Deserialize Binary Tree
```
Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

For example, you may serialize the following tree

    1
   / \
  2   3
     / \
    4   5
as "[1,2,3,null,null,4,5]", just the same as how LeetCode OJ serializes a binary tree. You do not necessarily need to follow this format, so please be creative and come up with different approaches yourself.
Note: Do not use class member/global/static variables to store states. Your serialize and deserialize algorithms should be stateless.
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
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        StringBuilder sb = new StringBuilder();
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        queue.add(root);
        while(!queue.isEmpty())
        {
            TreeNode cur = queue.poll();
            if(cur==null) sb.append("null,");
            else
            {
                sb.append(String.valueOf(cur.val)+",");
                 queue.add(cur.left);
                 queue.add(cur.right);
            }
        }
        
        return sb.toString();
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        if(data.length()==0) return null;
        String[] vals = data.split(",");
        int[] nums = new int[vals.length];
        TreeNode[] node = new TreeNode[vals.length];
        
        for(int i =0;i<vals.length;i++)
        {
            if(i>0)
            {
                nums[i] = nums[i-1];
            }
            if(vals[i].equals("null"))
            {
                node[i] = null;
                nums[i]++;
            }
            else
            {
                node[i] = new TreeNode(Integer.parseInt(vals[i]));
            }
        }
        
        for(int i =0;i<vals.length;i++)
        {
            if(node[i]==null) continue;
            node[i].left = node[2*(i-nums[i])+1];
            node[i].right = node[2*(i-nums[i])+2];
        }
        return node[0];
    }
}

```
