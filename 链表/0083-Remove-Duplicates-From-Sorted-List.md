

#### 1. 题目链接
[删除排序链表中的重复元素](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/)

#### 2. 题目描述
存在一个按升序排列的链表，给你这个链表的头节点 head ，请你删除所有重复的元素，使每个元素 只出现一次 。
返回同样按升序排列的结果链表。

#### 3. 解题思路

* 如果不偷窃最后一间房屋，则偷窃房屋的下标范围是 [0,n-2]；如果不偷窃第一间房屋，则偷窃房屋的下标范围是 [1,n-1]
* 然后使用打家劫舍的动态规划方法解决

#### 4. 编码实现
``` java
public ListNode deleteDuplicates(ListNode head) {
    ListNode cur = head;
    while (cur != null && cur.next != null) {
        if (cur.val == cur.next.val) {
            cur.next = cur.next.next;
        } else {
            cur = cur.next;
        }
    }
    return head;
}
```
