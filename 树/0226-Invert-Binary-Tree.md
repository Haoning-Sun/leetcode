

#### 1. 题目链接
[翻转二叉树](https://leetcode-cn.com/problems/invert-binary-tree/)

#### 2. 题目描述
翻转一棵二叉树。


#### 3. 解题思路
* 使用递归方法，先翻转左右子树，再交换左右子树位置

#### 4. 编码实现
``` java
public TreeNode invertTree(TreeNode root) {
    if (root == null) return root;
    TreeNode left = invertTree(root.left);
    TreeNode right = invertTree(root.right);
    root.left = right;
    root.right = left;
    return root;
}
```
