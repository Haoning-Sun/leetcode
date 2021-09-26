

#### 1. 题目链接
[求根节点到叶节点数字之和](https://leetcode-cn.com/problems/sum-root-to-leaf-numbers/)

#### 2. 题目描述
给你一个二叉树的根节点 root ，树中每个节点都存放有一个 0 到 9 之间的数字。
每条从根节点到叶节点的路径都代表一个数字：   
    * 例如，从根节点到叶节点的路径 1 -> 2 -> 3 表示数字 123 。
计算从根节点到叶节点生成的 所有数字之和 。


#### 3. 解题思路

* 

#### 4. 编码实现
``` java
public int sumNumbers(TreeNode root) {
    return dfs(root, 0);
}

public int dfs(TreeNode node, int preSum) {
    if (node == null) return 0;
    int sum = node.val + preSum * 10;
    if (node.left == null && node.right == null) {
        return sum;
    } else {
        return dfs(node.left, sum) + dfs(node.right, sum);
    }
}
```
