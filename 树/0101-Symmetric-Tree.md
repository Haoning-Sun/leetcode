

#### 1. 题目链接
[对称二叉树](https://leetcode-cn.com/problems/symmetric-tree/)

#### 2. 题目描述
给定一个二叉树，检查它是否是镜像对称的。

#### 3. 解题思路

* 递归
* 每个树的左子树与右子树镜像

#### 4. 编码实现
``` java
public boolean isSymmetric(TreeNode root) {
    return check(root, root);
}

public boolean check(TreeNode p, TreeNode q) {
    if (p == null && q == null) return true;
    if (p == null || q == null) return false;
    return p.val == q.val && check(p.left, q.right) && check(p.right, q.left);
}
```
