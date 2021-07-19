

#### 1. 题目链接
[寻找重复数](https://leetcode-cn.com/problems/find-the-duplicate-number/)

#### 2. 题目描述
给定一个包含n+1个整数的数组nums ，其数字都在1到n之间（包括1和n），可知至少存在一个重复的整数。

假设 nums 只有 一个重复的整数 ，找出 这个重复的数 。


#### 3. 解题思路
* 数组中有一个重复的整数相当于链表中存在环
* 找到数组中的重复整数相当于找到链表的环入口
* 使用双指针法
* 备注：设置链表长度为L，入口点距离头节点距离为a,快慢指针相遇点距离入口点为b,慢指针走的距离为s,环的长度为r,则可以得到以下公式：
    * 2s = s + nr (n为环的圈数)
    * s = a + b (慢指针从头节点走到相遇点)
    * r = L - a
    * 可转换为:(a + b = nr) => a = (nr - b) => a = (n - 1)r + (L - a - b)
      



#### 4. 编码实现
``` java
public int findDuplicate(int[] nums) {
    int slow = 0;
    int fast = 0;
    while (true) {
        slow = nums[slow];
        fast = nums[nums[fast]];
        if (slow == fast) {
            break;
        }
    }
    fast = 0;
    while (true) {
        slow = nums[slow];
        fast = nums[fast];
        if (slow == fast) {
            break;
        }
    }
    return slow;
}

```
