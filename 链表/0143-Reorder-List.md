

#### 1. 题目链接
[重排链表](https://leetcode-cn.com/problems/reorder-list/)

#### 2. 题目描述
给定一个单链表 L 的头节点 head ，单链表 L 表示为：

 L0 → L1 → … → Ln-1 → Ln 
请将其重新排列后变为：

L0 → Ln → L1 → Ln-1 → L2 → Ln-2 → …

不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

#### 3. 解题思路
* 寻找链表中点 + 链表逆序 + 合并链表

#### 4. 编码实现
``` java
public void reorderList(ListNode head) {
    if (head == null) return;    
    ListNode mid = middleNode(head);
    ListNode l1 = head;
    ListNode l2 = mid.next;
    mid.next = null;
    l2 = reverseList(l2);
    mergeList(l1, l2);
}

public ListNode middleNode(ListNode head) {
    ListNode fast = head, slow = head;
    while (fast.next != null && fast.next.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow;
}

public ListNode reverseList(ListNode head) {
    ListNode pre = null, next = null;
    while (head != null) {
        next = head.next;
        head.next = pre;
        pre = head;
        head = next;
    }
    return pre;
}

public void mergeList(ListNode l1, ListNode l2) {
    ListNode l1_next = null;
    ListNode l2_next = null;
    while (l1 != null && l2 != null) {
        l1_next = l1.next;
        l2_next = l2.next;
        l1.next = l2;
        l1 = l1_next;
        l2.next = l1;
        l2 = l2_next;
    }
}

```
