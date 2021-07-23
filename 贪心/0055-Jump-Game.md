

#### 1. 题目链接
[跳跃游戏](https://leetcode-cn.com/problems/jump-game/)

#### 2. 题目描述
给定一个非负整数数组 nums ，你最初位于数组的 第一个下标 。
数组中的每个元素代表你在该位置可以跳跃的最大长度。
判断你是否能够到达最后一个下标。

#### 3. 解题思路

* 贪心算法：从右向左迭代，对于每个节点我们检查是否存在一步跳跃可以到达 GOOD 的位置（currPosition + nums[currPosition] >= leftmostGoodIndex）。如果可以到达，当前位置也标记为 GOOD ，同时，这个位置将成为新的最左边的 GOOD 位置，一直重复到数组的开头，如果第一个坐标标记为 GOOD 意味着可以从第一个位置跳到最后的位置

#### 4. 编码实现
``` java
public boolean canJump(int[] nums) {
    int lastPos = nums.length - 1;
    for (int i = nums.length - 1; i >=0; i--) {
        if (i + nums[i] >= lastPos) {
            lastPos = i;
        }
    }
    return lastPos == 0;
}
```
