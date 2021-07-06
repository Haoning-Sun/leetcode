

#### 1. 题目链接
[ 环形链表 II](https://leetcode-cn.com/problems/linked-list-cycle-ii/)

#### 2. 题目描述
给定一个链表，返回链表开始入环的第一个节点。如果链表无环，则返回null。
为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。注意，pos 仅仅是用于标识环的情况，并不会作为参数传递到函数中。
说明：不允许修改给定的链表。



#### 3. 解题思路
* 设置两个指针，一个指针(慢)走一步，另一个指针(快)走两步，如果有环出现，则快指针能遇到慢指针
* 快指针重新回到头节点，两个指针每次均走一步，会在入环第一个节点相遇



#### 4. 编码实现
``` java
public ListNode detectCycle(ListNode head) {
    ListNode fast = head, slow = head;
    while(true) {
        if (fast == null || fast.next == null) return null;
        fast = fast.next.next;
        slow = slow.next;
        if (slow == fast) break;
    }
    fast = head;
    while (fast != slow) {
        fast = fast.next;
        slow = slow.next;
    }
    return fast;
}

```
