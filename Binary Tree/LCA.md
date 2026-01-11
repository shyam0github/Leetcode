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
## Illustration of how root return null and node  :

![Lowest Common Ancestor Illustration](../Image\LCAimage.png)

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

## Complexity Analysis

Time Complexity:
Each node is visited once → $O(n)$

Space Complexity:
Recursive stack depth → $O(h)$
where $h$ is the height of the tree

Worst case (skewed tree): $O(n)$

Best case (balanced tree): $O(\log n)$

---
