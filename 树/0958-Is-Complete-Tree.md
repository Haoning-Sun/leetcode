

#### 1. 题目链接
[二叉树的完全性检验](https://leetcode.cn/problems/check-completeness-of-a-binary-tree/)

#### 2. 题目描述
给定一个二叉树的 root ，确定它是否是一个 完全二叉树 。


#### 3. 解题思路

* 使用队列继续层次遍历
* 任意一个节点如果有右孩子而无左孩子则返回false
* 在符合上面条件情况下，如果遇到了第一个节点没有左或右孩子，则后续节点全部为叶子节点

#### 4. 编码实现
``` java
public boolean isCompleteTree(TreeNode root) {
    Queue<TreeNode> queue = new LinkedList<>();
    boolean leaf = false;
    TreeNode l = null;
    TreeNode r = null;
    queue.add(root);
    while (!queue.isEmpty()) {
        head = queue.poll();
        l = head.left;
        r = head.right;
        if ((leaf && (l != null || r != null)) ||
            (l == null && r != null)) {
                return false;
            }
        if (l != null) {
            queue.add(l);
        }
        if (r != null) {
            queue.add(r);
        }
        if (l == null || r == null) {
            leaf = true;
        }
    }
    return true;
}
```
