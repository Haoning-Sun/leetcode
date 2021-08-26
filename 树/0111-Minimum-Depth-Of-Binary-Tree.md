

#### 1. 题目链接
[二叉树的最小深度](https://leetcode-cn.com/problems/minimum-depth-of-binary-tree/)

#### 2. 题目描述
给定一个二叉树，找出其最小深度。。

#### 3. 解题思路

* 深度优先搜索

#### 4. 编码实现
``` java
public int minDepth(TreeNode root) {
    if (root == null) return 0;
    int left = minDepth(root.left);
    int right = minDepth(root.right);
    return root.left != null || root.right != null ? 1 + left + right : Math.min(left, right) + 1;
}
```
