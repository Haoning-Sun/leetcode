

#### 1. 题目链接
[删除排序链表中的重复元素 II](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/)

#### 2. 题目描述
存在一个按升序排列的链表，给你这个链表的头节点 head ，请你删除链表中所有存在数字重复情况的节点，只保留原始链表中没有重复出现的数字。
返回同样按升序排列的结果链表。

#### 3. 解题思路

* 创建哑结点dummyHead，指向头结点 
* cur指向链表的哑节点，随后开始对链表进行遍历
* 如果当前cur.next与cur.next.next对应的元素相同，那么我们就需要将cur.next以及所有后面拥有相同元素值的链表节点全部删除
* 我们记下这个元素值value，随后不断将cur.next 从链表中移除，直到 cur.next为空节点或者其元素值不等于value为止

#### 4. 编码实现
``` java
public ListNode deleteDuplicates(ListNode head) {
    if (head == null || head.next == null) return head;
    ListNode dummyHead = new ListNode(-1, head);
    ListNode cur = dummyHead;
    while (cur.next != null && cur.next.next != null) {
        if (cur.next.val == cur.next.next.val) {
            int value = cur.next.val;
            while (cur.next != null && cur.next.val == value) {
                cur.next = cur.next.next;
            }
        } else {
            cur = cur.next;
        }
    }
    return dummyHead.next;
}
```
