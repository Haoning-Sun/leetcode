

#### 1. 题目链接
[反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)

#### 2. 题目描述
给你单链表的头节点 head ，请你反转链表，并返回反转后的链表。


#### 3. 解题思路
* 迭代
* 将当前节点的next节点修改为指向前一个节点
* 需要保存下一个节点和前一个节点
#### 4. 编码实现
``` java
public ListNode reverseList(ListNode head) {
    ListNode pre = null;
    ListNode next = null;
    while (head != null) {
        next = head.next;
        head.next = pre;
        pre = head;
        head = next;
    }
    return pre;
}
```
