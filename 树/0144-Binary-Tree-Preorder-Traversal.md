

#### 1. 题目链接
[二叉树的前序遍历](https://leetcode-cn.com/problems/binary-tree-preorder-traversal/)

#### 2. 题目描述
给你二叉树的根节点 root ，返回它节点值的 前序 遍历。



#### 3. 解题思路
* 使用递归


#### 4. 编码实现
``` java
List<Integer> result = new ArrayList<>();
public List<Integer> inorderTraversal(TreeNode root) {
    if (root != null) {
        result.add(root.val);
        inorderTraversal(root.left);
        inorderTraversal(root.right);
    }
    return result;
}
```
