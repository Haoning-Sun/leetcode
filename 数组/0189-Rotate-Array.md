

#### 1. 题目链接
[旋转数组](https://leetcode-cn.com/problems/rotate-array/)

#### 2. 题目描述
给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。

#### 3. 解题思路
* 环形替代


#### 4. 编码实现
``` java
public void rotate(int[] nums, int k) {
    int len = nums.length;
    k = k % len;
    int count = 0;
    for (int start = 0; count < len; start++) {
        int cur = start;
        int pre = nums[cur];
        do {
            int next = (cur + k) % len;
            int tmp = nums[next];
            nums[next] = pre;
            pre = tmp;
            cur = next;
            count++;
        } while (start != cur);
    }
}
```
