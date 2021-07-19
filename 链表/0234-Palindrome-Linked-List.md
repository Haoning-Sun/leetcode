

#### 1. 题目链接
[回文链表](https://leetcode-cn.com/problems/palindrome-linked-list/)

#### 2. 题目描述
请判断一个链表是否为回文链表。

#### 3. 解题思路

* 使用双指针，快指针(走一步)和慢指针(走两步)
* 翻转前半个链表
* 快指针走到头后，依次判断慢指针和翻转链表两个链表

#### 4. 编码实现
``` java
public boolean isPalindrome(ListNode head) {
    ListNode fast = head;
    ListNode slow = head;
    ListNode cur = head;
    ListNode pre = null;
    
    while (fast != null && fast.next != null) {
        cur = slow;
        slow = slow.next;
        fast = fast.next.next;
        cur.next = pre;
        pre = cur;
    }
    
    if (fast != null) {
        slow = slow.next;
    }
    
    while (slow != null && cur != null) {
        if (cur.val != slow.val) {
            return false;
        }
        cur = cur.next;
        slow = slow.next;
    }
    return true;
}
```
