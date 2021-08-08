

#### 1. 题目链接
[最长连续序列](https://leetcode-cn.com/problems/longest-consecutive-sequence/)

#### 2. 题目描述
给定一个未排序的整数数组 nums ，找出数字连续的最长序列（不要求序列元素在原数组中连续）的长度。

#### 3. 解题思路

* 使用curCount记录一次连续数组的元素个数，使用max记录连续数组的最大值
* 先对数组排序
* 然后依次判断前后两个数组元素，更新curCount和max

#### 4. 编码实现
``` java
public int longestConsecutive(int[] nums) {
    if (nums == null || nums.length == 0) return 0;
    Arrays.sort(nums);
    int curCount = 1;
    int max = 0;
    for (int i = 1; i < nums.length; i++) {
        if (nums[i] - nums[i-1] == 1) {
            curCount++;
        } else if (nums[i] == nums[i-1]) {
            continue;
        } else {
            max = Math.max(max, curCount);
            curCount = 1;
        }
    }
    return Math.max(max, curCount);
}
```
