

#### 1. 题目链接
[二叉树的最大深度](https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/)

#### 2. 题目描述
给定一个二叉树，找出其最大深度。

#### 3. 解题思路

* 深度优先搜索

#### 4. 编码实现
``` java
public int maxDepth(TreeNode root) {
    if (root == null) return 0;
    if (root.left == null && root.right == null) return 1;
    int left = 0, right = 0;
    if (root.left != null) left = maxDepth(root.left) + 1;
    if (root.right != null) right = maxDepth(root.right) + 1;
    return Math.max(left, right);
}
```
