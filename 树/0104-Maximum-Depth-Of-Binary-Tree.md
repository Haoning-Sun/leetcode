

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
	return Math.max(maxDepth(root.left) + 1, maxDepth(root.right)+1);
}
```
