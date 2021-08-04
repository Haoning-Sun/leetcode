

#### 1. 题目链接
[最大子序和](https://leetcode-cn.com/problems/maximum-subarray/)

#### 2. 题目描述

给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

#### 3. 解题思路

* 动态规划：dp[i] = max(dp[i-1]+nums[i], nums[i])

#### 4. 编码实现
``` java
public int maxSubArray(int[] nums) {
    int[] dp = new int[nums.length];
    int ans = nums[0];
    dp[0] = nums[0];
    for (int i = 1; i < nums.length; i++) {
        dp[i] = Math.max(dp[i-1] + nums[i], nums[i]);
        ans = Math.max(ans, dp[i]);
    } 
    return ans;
}
```
