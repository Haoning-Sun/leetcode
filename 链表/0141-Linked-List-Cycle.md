

#### 1. 题目链接
[环形链表](https://leetcode-cn.com/problems/linked-list-cycle/)

#### 2. 题目描述
给定一个链表，判断链表中是否有环。

如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。注意：pos 不作为参数进行传递，仅仅是为了标识链表的实际情况。

如果链表中存在环，则返回 true 。 否则，返回 false 。


#### 3. 解题思路
* 设置两个指针，一个指针(慢)走一步，另一个指针(快)走两步，如果有环出现，则快指针能遇到慢指针



#### 4. 编码实现
``` java
public boolean hasCycle(ListNode head) {
    ListNode s = head, f = head;
    while (f != null && f.next != null) {
        s = s.next;
        f = f.next.next;
        if (s == f) {
            return true;
        }
    }   
    return false;
}

```
