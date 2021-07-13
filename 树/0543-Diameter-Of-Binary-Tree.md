

#### 1. 题目链接
[二叉树的直径](https://leetcode-cn.com/problems/diameter-of-binary-tree/)

#### 2. 题目描述
给定一棵二叉树，你需要计算它的直径长度。一棵二叉树的直径长度是任意两个结点路径长度中的最大值。这条路径可能穿过也可能不穿过根结点。

#### 3. 解题思路
* 假设我们知道对于该节点的左儿子向下遍历经过最多的节点数L（即以左儿子为根的子树的深度）和其右儿子向下遍历经过最多的节点数R（即以右儿子为根的子树的深度），那么以该节点为起点的路径经过节点数的最大值即为 L+R+1
* dfs用于深度遍历计算某节点左右子树的最大深度


#### 4. 编码实现
``` java
public int ans = 0;
public int diameterOfBinaryTree(TreeNode root) {
    dfs(root);
    return ans;
}

public int dfs(TreeNode root) {
    if (root == null) return 0;
    int l = dfs(root.left);
    int r = dfs(root.right);
    ans = Math.max(ans, l + r);
    return Math.max(l, r) + 1;
}
```
