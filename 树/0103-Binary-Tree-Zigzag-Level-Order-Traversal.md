

#### 1. 题目链接
[二叉树的锯齿形层序遍历](https://leetcode-cn.com/problems/binary-tree-zigzag-level-order-traversal/)

#### 2. 题目描述
给定一个二叉树，返回其节点值的锯齿形层序遍历。（即先从左往右，再从右往左进行下一层遍历，以此类推，层与层之间交替进行）。

#### 3. 解题思路

* 广度优先搜索，需要使用双端队列，每次判断应入队的位置

#### 4. 编码实现
``` java
public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
    List<List<Integer>> ans = new LinkedList<>();
    if (root == null) return ans;
    Queue<TreeNode> queue = new LinkedList<>();
    queue.add(root);
    boolean isLeftOrder = true;
    while (!queue.isEmpty()) {
        int level = queue.size();
        Deque<Integer> list = new LinkedList<>();
        for (int i = 0; i < level; i++) {
            TreeNode node = queue.poll();
            if (isLeftOrder) {
                list.addLast(node.val);
            } else {
                list.addFirst(node.val);
            }
            if (node.left != null) queue.add(node.left);
            if (node.right != null) queue.add(node.right);
        }
        ans.add(new LinkedList(list));
        isLeftOrder = !isLeftOrder;
    } 
    return ans;
}
```
