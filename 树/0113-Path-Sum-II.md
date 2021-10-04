

#### 1. 题目链接
[路径总和 II](https://leetcode-cn.com/problems/path-sum-ii/)

#### 2. 题目描述
给你二叉树的根节点 root 和一个整数目标和 targetSum ，找出所有 从根节点到叶子节点 路径总和等于给定目标和的路径。

#### 3. 解题思路

* 回溯法

#### 4. 编码实现
``` java
List<List<Integer>> result = new ArrayList<>();
public List<List<Integer>> pathSum(TreeNode root, int targetSum) {
    if (root != null) {
        dfs(root, targetSum, new ArrayList<Integer>());
    }
    return result;
}

public void dfs(TreeNode root, int target, List<Integer> path) {
    path.add(root.val);
    if (root.left == null && root.right == null) {
        if (target == root.val) {
            result.add(new ArrayList<>(path));
        }
    }
    if (root.left != null) {
        dfs(root.left, target - root.val, path);
        path.remove(path.size() - 1);
    }
    if (root.right != null) {
        dfs(root.right, target - root.val, path);
        path.remove(path.size() - 1);
    }
}
```
