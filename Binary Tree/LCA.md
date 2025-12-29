# LCA of Binary Tree

```java 

class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
      if(root == null || root == p || root == q)

      return root;

      TreeNode left = lowestCommonAncestor(root.left, p, q);

      TreeNode right = lowestCommonAncestor(root.right, p, q);

      if(left != null && right != null)

      return root;
      return left != null ?  left: right;
    }
}

```


![[Pasted image 20251229160231.png]]
#### Traverse in PostOrder Traversal (left, Right, Root)
### Base
if current node is 
```
node == p or node == q 
return node
```

##### cond 1
if <span style="color:rgb(255, 255, 0)">any side</span> gives any node that we are trying to find LCA <span style="color:rgb(255, 255, 0)">return that node</span>.
and if <span style="color:rgb(255, 255, 0)">both side</span> return <span style="color:rgb(223, 114, 238)">null</span> then <span style="color:rgb(223, 114, 238)">null returns</span> 

##### cond 2
else
if <span style="color:rgb(255, 255, 0)">both side</span> returning node then return <span style="color:rgb(255, 255, 0)">current node</span> 

---
