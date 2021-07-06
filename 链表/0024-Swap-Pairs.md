

#### 1. 题目链接
[两两交换链表中的节点](https://leetcode-cn.com/problems/swap-nodes-in-pairs/)

#### 2. 题目描述
给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。
你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。


#### 3. 解题思路
* 思路一：递归
* 思路二：迭代
  * 创建哑结点 dummyHead，令 dummyHead.next = head。令 temp 表示当前到达的节点，初始时 temp = dummyHead。每次需要交换 temp 后面的两个节点
  * 如果 temp 的后面没有节点或者只有一个节点，则没有更多的节点需要交换，因此结束交换。否则，获得 temp 后面的两个节点 node1 和 node2，通过更新节点的指针关系实现两两交换节点。
  * 交换之前的节点关系是temp -> node1 -> node2，交换之后的节点关系要变成 temp -> node2 -> node1

#### 4. 编码实现

``` java

/**
 * 递归
 * 空间复杂度O(N)，时间复杂度O(N)
 */
public ListNode swapPairs(ListNode head) {
    if (head == null || head.next == null) {
        return head;
    }
    ListNode newHead = head.next;
    head.next = swapPairs(newHead.next);
    newHead.next = head;
    return newHead;
}
```

``` java
/**
 * 迭代
 * 空间复杂度O(1)，时间复杂度O(N)
 */
public ListNode swapPairs(ListNode head) {
    ListNode dummyNode = new ListNode(0);
    dummyNode.next = head;
    ListNode tmp = dummyNode;
    while (tmp.next != null && tmp.next.next != null) {
        ListNode node1 = tmp.next;
        ListNode node2 = tmp.next.next;
        tmp.next = node2;
        node1.next = node2.next;
        node2.next = node1;
        tmp = node1;
    }
    return dummyNode.next;
}
```
