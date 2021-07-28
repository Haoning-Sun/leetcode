

#### 1. 题目链接
[反转链表 II](https://leetcode-cn.com/problems/reverse-linked-list-ii/)

#### 2. 题目描述
给你单链表的头指针 head 和两个整数left 和 right ，其中left <= right 。请你反转从位置 left 到位置 right 的链表节点，返回 反转后的链表 。


#### 3. 解题思路

* curr：指向待反转区域的第一个节点left；
* next：永远指向 curr 的下一个节点，循环过程中，curr 变化以后 next 会变化；
* pre：永远指向待反转区域的第一个节点 left 的前一个节点，在循环过程中不变；
* 每次将待反转的链表节点插入到pre后面；


#### 4. 编码实现
``` java
public ListNode reverseBetween(ListNode head, int left, int right) {
    ListNode dummyNode = new ListNode(-1);
    dummyNode.next = head;
    ListNode pre = dummyNode;
    for (int i = 0; i < left - 1; i++) {
        pre = pre.next;
    }  
     ListNode cur = pre.next, next = null;
    for (int j = 0; j < right - left; j++) {
        next = cur.next;
        cur.next = next.next;
        next.next = pre.next;
        pre.next = next;
    }
    return dummyNode.next;
}
```
