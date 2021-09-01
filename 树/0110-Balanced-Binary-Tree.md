

#### 1. 题目链接
[平衡二叉树](https://leetcode-cn.com/problems/balanced-binary-tree/)

#### 2. 题目描述
给定一个二叉树，判断它是否是高度平衡的二叉树。

#### 3. 解题思路

* 递归判断子树是否平衡

#### 4. 编码实现
``` java
public boolean isBalanced(TreeNode root) {
    if (root == null) return true;
    return Math.abs(height(root.left) - height(root.right)) <=1 && isBalanced(root.left) && isBalanced(root.right);
}

public int height(TreeNode root) {
    if (root == null) return 0;
    return Math.max(height(root.left)+1, height(root.right)+1);
}
```
