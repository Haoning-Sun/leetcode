

#### 1. 题目链接
[路径总和](https://leetcode-cn.com/problems/path-sum/)

#### 2. 题目描述
给你二叉树的根节点root 和一个表示目标和的整数targetSum ，判断该树中是否存在 根节点到叶子节点 的路径，这条路径上所有节点值相加等于目标和targetSum 。

#### 3. 解题思路

* dfs

#### 4. 编码实现
``` java
public boolean hasPathSum(TreeNode root, int targetSum) {
    if (root == null) return false;
    if (root.left == null && root.right == null) {
        return root.val == targetSum;
    }
    return hasPathSum(root.left, targetSum - root.val) || hasPathSum(root.right, targetSum - root.val);
}
```
