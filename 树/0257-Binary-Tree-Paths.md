

#### 1. 题目链接
[二叉树的所有路径](https://leetcode-cn.com/problems/binary-tree-paths/)

#### 2. 题目描述
给你一个二叉树的根节点 root ，按 任意顺序 ，返回所有从根节点到叶子节点的路径。

#### 3. 解题思路

* 深度优先搜索

#### 4. 编码实现
``` java
List<String> result = new ArrayList<>();
public List<String> binaryTreePaths(TreeNode root) {
    if (root == null) return result;
    List<Integer> path = new ArrayList<>();
    dfs(root, path);
    return result;
}

public void dfs(TreeNode root, List<Integer> path) {
    path.add(root.val);
    if (root.left != null) {
        dfs(root.left, new ArrayList<>(path));
    } 
    if (root.right != null) {
        dfs(root.right, new ArrayList<>(path));
    }
    if (root.left == null && root.right == null) {
        StringJoiner joiner = new StringJoiner("->");
        for (int num : path) {
            joiner.add(String.valueOf(num));
        }
        result.add(joiner.toString());
    }
}
```
