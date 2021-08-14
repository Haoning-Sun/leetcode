

#### 1. 题目链接
[奇偶链表](https://leetcode-cn.com/problems/odd-even-linked-list/)

#### 2. 题目描述


#### 3. 解题思路

* 维护两个指针odd和even分别指向奇数节点和偶数节点，初始时 odd = head，even = evenHead。通过迭代的方式将奇数节点和偶数节点分离成两个链表，每一步首先更新奇数节点，然后更新偶数节点
* 更新奇数节点时，奇数节点的后一个节点需要指向偶数节点的后一个节点，因此令 odd.next = even.next，然后令 odd = odd.next，此时 odd 变成 even 的后一个节点。
* 更新偶数节点时，偶数节点的后一个节点需要指向奇数节点的后一个节点，因此令 even.next = odd.next，然后令 even = even.next，此时 even 变成 odd 的后一个节点。
* 最后令odd.next = evenHead，将偶数链表连接在奇数链表之后，结果链表的头节点仍然是 head

#### 4. 编码实现
``` java
public ListNode oddEvenList(ListNode head) {
    if (head == null) return head;
    ListNode odd = head, even = head.next, evenHead = even;
    while (odd != null && odd.next != null) {
        odd.next = even.next;
        odd = odd.next;
        even.next = odd.next;
        even = even.next;
    }
    odd.next = evenHead;
    return head;
}
```
