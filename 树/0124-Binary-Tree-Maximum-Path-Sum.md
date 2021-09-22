

#### 1. 题目链接
[二叉树中的最大路径和](https://leetcode-cn.com/problems/binary-tree-maximum-path-sum/)

#### 2. 题目描述
路径 被定义为一条从树中任意节点出发，沿父节点-子节点连接，达到任意节点的序列。同一个节点在一条路径序列中 至多出现一次 。该路径 至少包含一个 节点，且不一定经过根节点。
路径和 是路径中各节点值的总和。
给你一个二叉树的根节点 root ，返回其 最大路径和 。

#### 3. 解题思路

* 递归

#### 4. 编码实现
``` java

int maxSum = Integer.MIN_VALUE;
public int maxPathSum(TreeNode root) {
    maxGain(root);
    return maxSum;
}

public int maxGain(TreeNode node) {
    if (node == null) return 0;
    int leftSum = Math.max(maxGain(node.left), 0);
    int rightSum = Math.max(maxGain(node.right), 0);
    int newSum = leftSum + rightSum + node.val;
    maxSum = Math.max(maxSum, newSum);
    return node.val + Math.max(leftSum, rightSum);
}
```
