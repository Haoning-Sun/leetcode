

#### 1. 题目链接
[相交链表](https://leetcode-cn.com/problems/intersection-of-two-linked-lists/)

#### 2. 题目描述
给你两个单链表的头节点headA和headB，请你找出并返回两个单链表相交的起始节点。如果两个链表没有交点，返回 null 。

#### 3. 解题思路
* 双指针法：若相交，在走过相同长度(两段各自的部分加上对方不重叠的部分)后会相遇

#### 4. 编码实现
``` java
public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
    ListNode a = headA, b = headB;
    while (a != b) {
        a = (a != null) ? a.next : headB;
        b = (b != null) ? b.next : headA;
    }
    return a;
}
```
