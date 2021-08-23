

#### 1. 题目链接
[删除链表的倒数第 N 个结点](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/)

#### 2. 题目描述
给你一个链表，删除链表的倒数第 n 个结点，并且返回链表的头结点。

#### 3. 解题思路

* 使用双指针

#### 4. 编码实现
``` java
public ListNode removeNthFromEnd(ListNode head, int n) {
    ListNode dummyHead = new ListNode(0);
    dummyHead.next = head;
    ListNode slow = dummyHead, fast = dummyHead;
    for (int i = 0; i<=n; i++) {
        fast = fast.next;
    }
    while (fast != null) {
        fast = fast.next;
        slow = slow.next;
    }
    slow.next = slow.next.next;
    return dummyHead.next;
}
```
