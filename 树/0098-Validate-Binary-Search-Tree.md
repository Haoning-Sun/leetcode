

#### 1. 题目链接
[验证二叉搜索树](https://leetcode-cn.com/problems/validate-binary-search-tree/)

#### 2. 题目描述
* 给定一个二叉树，判断其是否是一个有效的二叉搜索树。
* 假设一个二叉搜索树具有如下特征：
    * 节点的左子树只包含小于当前节点的数。
    * 节点的右子树只包含大于当前节点的数。
    * 所有左子树和右子树自身必须也是二叉搜索树。

#### 3. 解题思路
* 非递归：中序遍历，判断是否大于前一次访问的val
* 递归：进入左子树将parent.val设置为upper，进入右子树将parent.val设置为lower

#### 4. 编码实现
``` java

/**
 * 非递归
 */
public boolean isValidBST(TreeNode root) {
    Stack<TreeNode> stack = new Stack<TreeNode>();
    long inorder = Long.MIN_VALUE;
    while (!stack.empty() || root != null) {
        while (root != null) {
            stack.push(root);
            root = root.left;
        }
        root = stack.pop();
        if (root.val <= inorder) {
            return false;
        }
        inorder = root.val;
        root = root.right;
    }
    return true;
}

/**
 * 递归
 */
public boolean isValidBST(TreeNode root) { 
   return isValidBST(root, Long.MIN_VALUE, Long.MAX_VALUE);
}

public boolean isValidBST(TreeNode node, long lower, long upper) {
    if (node == null) return true;
    if (node.val <= lower || node.val >= upper) return false;
    return isValidBST(node.left, lower, node.val) && isValidBST(node.right, node.val, upper);
}
```
