

#### 1. 题目链接
[二叉树的后序遍历](https://leetcode.cn/problems/binary-tree-postorder-traversal/)

#### 2. 题目描述
给你一棵二叉树的根节点 root ，返回其节点值的 后序遍历 。

#### 3. 解题思路
* 使用递归
* 使用非递归


#### 4. 编码实现
``` java
List<Integer> result = new ArrayList<>();
public List<Integer> postorderTraversal(TreeNode root) {
    if (root != null) {
        inorderTraversal(root.left);
        inorderTraversal(root.right);
        result.add(root.val);
    }
    return result;
}

public List<Integer> postorderTraversal(TreeNode root) {
    Stack<TreeNode> s1 = new Stack<TreeNode>();
    Stack<TreeNode> s2 = new Stack<TreeNode>();
    List<Integer> result = new ArrayList<>();
    if (root != null) {
        s1.push(root);
        while (!s1.isEmpty()) {
            root = s1.pop();
            s2.push(root);
            if (root.left != null) {
                s1.push(root.left);
            }
            if (root.right != null) {
                s1.push(root.right);
            }
        }
        while (!s2.isEmpty()) {
            result.add(s2.pop().val);
        }
    }
    return result;
}
```
