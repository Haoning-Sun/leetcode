

#### 1. 题目链接
[链表的中间结点](https://leetcode-cn.com/problems/middle-of-the-linked-list/)

#### 2. 题目描述
给定一个头结点为 head 的非空单链表，返回链表的中间结点。
如果有两个中间结点，则返回第二个中间结点。

#### 3. 解题思路

* 使用快慢指针

#### 4. 编码实现
``` java
public ListNode middleNode(ListNode head) {
    ListNode fast = head, slow = head;
    while (fast != null && fast.next != null) {
        fast = fast.next.next;
        slow = slow.next;
    }
    return slow;
}
```
