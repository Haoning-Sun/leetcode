#### 1. 题目链接
[复制带随机指针的链表](https://leetcode.cn/problems/copy-list-with-random-pointer/)

#### 2. 题目描述
给你一个长度为 n 的链表，每个节点包含一个额外增加的随机指针 random ，该指针可以指向链表中的任何节点或空节点。

构造这个链表的 深拷贝。 深拷贝应该正好由 n 个 全新 节点组成，其中每个新节点的值都设为其对应的原节点的值。新节点的 next 指针和 random 指针也都应指向复制链表中的新节点，并使原链表和复制链表中的这些指针能够表示相同的链表状态。复制链表中的指针都不应指向原链表中的节点 。

#### 3. 解题思路

1. 将新节点设置为所拷贝的原节点的next节点；
2. 根据原节点的random和next值依次循环修改新节点的random和next节点。

#### 4. 编码实现
``` java
public Node copyRandomList(Node head) {
    if (head == null) {
        return head;
    }
    Node cur = head;
    Node next = null;
    while (cur != null) {
        next = cur.next;
        cur.next = new Node(cur.val);
        cur.next.next = next;
        cur = next;
    }
    cur = head;
    Node curCopy = null;
    while (cur != null) {
        next = cur.next.next;
        curCopy = cur.next;
        curCopy.random = cur.random != null ? cur.random.next : null;
        cur = next;
    }
    Node res = head.next;
    cur = head;
    while (cur != null) {
        next = cur.next.next;
        curCopy = cur.next; 
        curCopy.next = next != null ? next.next : null;
        cur.next = next;
        cur = next;
    }
    return res;
}
```