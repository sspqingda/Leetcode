#Populating Next Right Pointers in Each Node
```
Given a binary tree

    struct TreeLinkNode {
      TreeLinkNode *left;
      TreeLinkNode *right;
      TreeLinkNode *next;
    }
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.

Note:

You may only use constant extra space.
You may assume that it is a perfect binary tree (ie, all leaves are at the same level, and every parent has two children).
For example,
Given the following perfect binary tree,
         1
       /  \
      2    3
     / \  / \
    4  5  6  7
After calling your function, the tree should look like:
         1 -> NULL
       /  \
      2 -> 3 -> NULL
     / \  / \
    4->5->6->7 -> NULL

```


#117. Populating Next Right Pointers in Each Node II
Follow up for problem "Populating Next Right Pointers in Each Node".

What if the given tree could be any binary tree? Would your previous solution still work?

Note:

You may only use constant extra space.
For example,
Given the following binary tree,
         1
       /  \
      2    3
     / \    \
    4   5    7
After calling your function, the tree should look like:
         1 -> NULL
       /  \
      2 -> 3 -> NULL
     / \    \
    4-> 5 -> 7 -> NULL
    
    
```
```java
/**
 * Definition for binary tree with next pointer.
 * public class TreeLinkNode {
 *     int val;
 *     TreeLinkNode left, right, next;
 *     TreeLinkNode(int x) { val = x; }
 * }
 */
public class Solution {
    public void connect(TreeLinkNode root) {
        Queue<TreeLinkNode> queue = new LinkedList<TreeLinkNode>();
        if(root==null) return;
        queue.add(root);
        queue.add(null);
        while(!queue.isEmpty())
        {
            TreeLinkNode cur = queue.poll();
            while(cur!=null)
            {
                cur.next = queue.peek();
                if(cur.left!=null) queue.add(cur.left);
                if(cur.right!=null) queue.add(cur.right);
                cur = queue.poll();
            }
            if(!queue.isEmpty())
            {
                queue.add(null);
            }
        }
       
        return;
    }
}
```


```java
public class Solution {
    public void connect(TreeLinkNode root) {
        if(root==null) return;
        TreeLinkNode first = root;
        while(first !=null) 
        {
            TreeLinkNode cur = first;
            while(cur!=null)
            {
                if(cur.left!=null)cur.left.next = cur.right;
                if(cur.right!=null && cur.next!=null) cur.right.next = cur.next.left;
                cur = cur.next;
            }
            first = first.left;
        }
    }
       
      
}

```



``` java
public class Solution {
    public void connect(TreeLinkNode root) {
        if(root ==null) return;
        TreeLinkNode first = root;
        while(first!=null)
        {
            TreeLinkNode cur = first;
            while(cur != null)
            {
                TreeLinkNode next = cur.next;
                while(next!=null&&next.left==null&&next.right==null) next = next.next;
                TreeLinkNode nextChild = null;
                if(next!=null) {
                    nextChild = (next.left!=null?next.left:next.right);
                }
                if(cur.left!=null&&cur.right!=null)
                {
                    cur.left.next = cur.right;
                    cur.right.next = nextChild;
                }
                else if (cur.left!=null)
                {
                   cur.left.next = nextChild;
                }
                else if(cur.right!=null)
                {
                    cur.right.next = nextChild;
                }
                
                cur = next;
            }
            
            while(first!=null && first.left == null && first.right ==null) first = first.next;
            if(first!=null){
                first = (first.left!=null?first.left:first.right);
            }
            
        }
        
    }
}
```

```java

public class Solution {
    public void connect(TreeLinkNode root) {
        while(root != null){
            TreeLinkNode tempChild = new TreeLinkNode(0);
            TreeLinkNode currentChild = tempChild;
            while(root!=null){
                if(root.left != null) { currentChild.next = root.left; currentChild = currentChild.next;}
                if(root.right != null) { currentChild.next = root.right; currentChild = currentChild.next;}
                root = root.next;
            }
            root = tempChild.next;
            tempChild.next = null;
        }
    }
}

```
