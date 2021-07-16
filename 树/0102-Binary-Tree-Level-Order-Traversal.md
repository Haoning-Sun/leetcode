

#### 1. 题目链接
[二叉树的层序遍历](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/)

#### 2. 题目描述
给你一个二叉树，请你返回其按 层序遍历 得到的节点值。 （即逐层地，从左到右访问所有节点）。


#### 3. 解题思路
* 使用队列保存数据
* 第一层只有root一个节点，从队列取出，放入root的left和right，此时队列中只有root的left和right，也位于同一层；
* 按上面描述，每次取出队列全部的node都位于一层，其node的left和right也都位于一层

#### 4. 编码实现
``` java
public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> ans = new ArrayList();
    if (root == null) return ans;
    Queue<TreeNode> queue = new LinkedList<TreeNode>();
    queue.add(root);
    while (!queue.isEmpty()) {
        int level = queue.size();
        List<Integer> list = new ArrayList();
        for (int i = 1; i <= level; i++) {
            TreeNode cur = queue.poll();
            list.add(cur.val);
            if (cur.left != null) {
                queue.add(cur.left);
            }
            if (cur.right != null) {
                queue.add(cur.right);
            }
        }
        ans.add(list);
    }
    return ans;
}
```
