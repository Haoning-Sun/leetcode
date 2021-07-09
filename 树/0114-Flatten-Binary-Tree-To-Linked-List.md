

#### 1. 题目链接
[二叉树展开为链表](https://leetcode-cn.com/problems/flatten-binary-tree-to-linked-list/)

#### 2. 题目描述
给你二叉树的根结点 root ，请你将它展开为一个单链表：

展开后的单链表应该同样使用 TreeNode ，其中 right 子指针指向链表中下一个结点，而左子指针始终为 null 。
展开后的单链表应该与二叉树 先序遍历 顺序相同。


#### 3. 解题思路
* 前序遍历二叉树加入list中
* 遍历list取出节点构造链表



#### 4. 编码实现
``` java
public void flatten(TreeNode root) {
    List<TreeNode> list = new ArrayList<>();
    preorderTraversal(root, list);
    for (int i = 1; i < list.size(); i++) {
        TreeNode pre = list.get(i - 1);
        TreeNode cur = list.get(i);
        pre.left = null;
        pre.right = cur;
    }
}

public void preorderTraversal(TreeNode root, List<TreeNode> list) {
    if (root != null) {
        list.add(root);
        preorderTraversal(root.left, list);
        preorderTraversal(root.right, list);
    }
}
```
