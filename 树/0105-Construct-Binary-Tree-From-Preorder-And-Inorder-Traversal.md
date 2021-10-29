

#### 1. 题目链接
[从前序与中序遍历序列构造二叉树](https://leetcode-cn.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

#### 2. 题目描述
给定一棵树的前序遍历 preorder 与中序遍历  inorder。请构造二叉树并返回其根节点。

#### 3. 解题思路

* 递归

#### 4. 编码实现
``` java
public TreeNode buildTree(int[] preorder, int[] inorder) {
    if (inorder == null || inorder.length == 0 || preorder == null || preorder.length == 0) {
        return null;
    }

    TreeNode root = buildTree(preorder, 0, preorder.length - 1, inorder, 0, inorder.length - 1);
    return root;
}
    public TreeNode buildTree(int[] preorder, int preStart, int preEnd, int[] inorder, int inStart, int inEnd) {
        TreeNode root = new TreeNode(preorder[preStart]);
        if (inStart == inEnd || preStart == preEnd) {
            return root;
        }
        for (int index = inStart; index <= inEnd; index++) {
            if (inorder[index] == preorder[preStart]) {
                int lChildLen = index - inStart;
                int rChildLen = inEnd - index;
                 if (lChildLen > 0) {
                    root.left = buildTree(preorder, preStart + 1, preStart + lChildLen, 
                    inorder,inStart, index - 1);
                 }
                if (rChildLen > 0) {
                    root.right = buildTree(preorder,
                    preStart + lChildLen + 1, preEnd, inorder, index + 1, inEnd);
                }
                break;
            }
        }
        return root;
    }

```
