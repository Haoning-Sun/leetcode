

#### 1. 题目链接
[二叉树的最近公共祖先](https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree/)

#### 2. 题目描述
给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。

#### 3. 解题思路
* 递归左右子树
* 当root等于p或q时则直接返回root，否则返回null
* 结果
    * 当left和right同时为空：说明root的左/右子树中都不包含 p,q，返回null；
    * 当 left和right同时不为空：说明 p, q分列在root的异侧（分别在左 / 右子树），因此root为最近公共祖先，返回root；
    * 当 left为空 ，right不为空 ：p,q都不在root的左子树中，直接返回right。具体可分为两种情况：
      * p,q其中一个在root的右子树中，此时right指向p（假设为p）；
      * p,q两节点都在root的右子树中，此时的right指向最近公共祖先节点；
    * 当left不为空 ，right为空 ：与上述同理；
      

#### 4. 编码实现
``` java
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null || root == p || root == q) return root;
    TreeNode left = lowestCommonAncestor(root.left, p, q);
    TreeNode right = lowestCommonAncestor(root.right, p, q);
    if (left == null) return right;
    if (right == null) return left;
    return root;
}
```
