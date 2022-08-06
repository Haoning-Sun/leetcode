

#### 1. 题目链接
[二叉树的前序遍历](https://leetcode-cn.com/problems/binary-tree-preorder-traversal/)

#### 2. 题目描述
给你二叉树的根节点root，返回它节点值的前序遍历。



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

public List<Integer> inorderTraversal(TreeNode root) {
    Stack<TreeNode> stack = new Stack<TreeNode>();
    List<Integer> result = new ArrayList<>();
    if (root == null) return result;
    stack.push(root);
    while (stack.size() != 0) {
        TreeNode node = stack.pop();
        result.add(node.val);
        if (node.right != null) {
            stack.push(node.right);
        }
        if (node.left != null) {
            stack.push(node.left);
        }
    }
    return result;
}
```
