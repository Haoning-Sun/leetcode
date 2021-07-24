

#### 1. 题目链接
[对链表进行插入排序](https://leetcode-cn.com/problems/insertion-sort-list/)

#### 2. 题目描述
对链表进行插入排序。


#### 3. 解题思路
* 从前往后找插入点

#### 4. 编码实现
``` java
public ListNode insertionSortList(ListNode head) {
    if (head == null) return head;
    ListNode dummyHead = new ListNode(0);
    ListNode cur = head.next, lastSortedNode = head;
    dummyHead.next = head;
    
    while (cur != null) {
        if (lastSortedNode.val <= cur.val) {
            lastSortedNode = lastSortedNode.next;
        } else {
            ListNode pre = dummyHead;
            while (pre.next.val <= cur.val) {
                pre = pre.next;
            }
            lastSortedNode.next = cur.next;
            cur.next = pre.next;
            pre.next = cur;
        }
        cur = lastSortedNode.next;
    }
    return dummyHead.next;
}
```
