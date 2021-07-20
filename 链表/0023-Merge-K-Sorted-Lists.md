

#### 1. 题目链接
[合并K个升序链表](https://leetcode-cn.com/problems/merge-k-sorted-lists/)

#### 2. 题目描述
给你一个链表数组，每个链表都已经按升序排列。

请你将所有链表合并到一个升序链表中，返回合并后的链表。


#### 3. 解题思路

* 思路一：使用分治思想，每次merge两个链表
* 思路二：使用优先级队列

#### 4. 编码实现
``` java
public ListNode mergeKLists(ListNode[] lists) {
    return merge(lists, 0, lists.length - 1);
}

public ListNode merge(ListNode[] lists, int l, int r) {
    if (l == r) {
        return lists[l];
    }
    if (l > r) {
        return null;
    }
    int mid = (l + r)>>1;
    return mergeTwoLists(merge(lists, l, mid), merge(lists, mid+1, r));
}

public ListNode mergeTwoLists(ListNode a, ListNode b) {
    if (a == null || b == null) return a != null ? a : b;
    ListNode head = new ListNode(0);
    ListNode tail = head, aPtr = a, bPtr = b;
    
    while (aPtr != null && bPtr != null) {
        if (aPtr.val < bPtr.val) {
            tail.next = aPtr;
            aPtr = aPtr.next;
        } else {
            tail.next = bPtr;
            bPtr = bPtr.next;
        }
        tail = tail.next;
    }
    tail.next = (aPtr != null ? aPtr : bPtr);
    return head.next;
}
```
