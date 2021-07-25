

#### 1. 题目链接
[最短无序连续子数组](https://leetcode-cn.com/problems/shortest-unsorted-continuous-subarray/)

#### 2. 题目描述
给你一个整数数组 nums ，你需要找出一个 连续子数组 ，如果对这个子数组进行升序排序，那么整个数组都会变为升序排序。
请你找出符合题意的 最短 子数组，并输出它的长度。

#### 3. 解题思路
* 从左到右循环，记录最大值为 max，若 nums[i] < max, 则表明位置 i 需要调整, 循环结束，记录需要调整的最大位置 i 为 rightBound
* 同理，从右到左循环，记录最小值为 min, 若 nums[i] > min, 则表明位置 i 需要调整，循环结束，记录需要调整的最小位置 i 为 leftBound

#### 4. 编码实现
``` java
public int findUnsortedSubarray(int[] nums) {
    int rightBound = -1;
    int leftMax = Integer.MIN_VALUE;
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] < leftMax) {
            rightBound = i;
        } else {
            leftMax = nums[i];
        }
    }
    int leftBound = nums.length;
    int rightMax = Integer.MAX_VALUE;
    for (int j = nums.length - 1; j >= 0; j--) {
        if (nums[j] > rightMax) {
            leftBound = j;
        } else {
            rightMax = nums[j];
        }
    }
    return Math.max(0, rightBound - leftBound + 1);
}
```
