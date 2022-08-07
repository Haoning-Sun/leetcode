

#### 1. 题目链接
[二叉树的中序遍历](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/)

#### 2. 题目描述
给定一个二叉树的根节点 root ，返回它的 中序 遍历。



#### 3. 解题思路
* 使用递归


#### 4. 编码实现
``` java
List<Integer> result = new ArrayList<>();
public List<Integer> inorderTraversal(TreeNode root) {
    if (root != null) {
        inorderTraversal(root.left);
        result.add(root.val);
        inorderTraversal(root.right);
    }
    return result;
}

public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    Stack<TreeNode> stack = new Stack<>();
    if (root == null) return result;
    while (root != null || !stack.isEmpty()) {
        if (root != null) {
            stack.push(root);
            root = root.left;
        } else {
            root = stack.pop();
            result.add(root.val);
            root = root.right;
        }
    }
    return result;
}
```
