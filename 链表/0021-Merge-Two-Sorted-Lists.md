

#### 1. 题目链接
[合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)

#### 2. 题目描述
将两个升序链表合并为一个新的 升序 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。


#### 3. 解题思路
* 使用递归；
* 每次比较后返回较小的结点，该结点next从剩下的两个链表中选择(使用递归)；


#### 4. 编码实现
``` java
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    if (l1 == null) {
        return l2;
    }
    if (l2 == null) {
        return l1;
    }
    if (l1.val < l2.val) {
        l1.next = mergeTwoLists(l1.next, l2);
        return l1;
    } else {
        l2.next = mergeTwoLists(l1, l2.next);
        return l2;
    }
}
```
