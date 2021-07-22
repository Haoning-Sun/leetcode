

#### 1. 题目链接
[最长递增子序列](https://leetcode-cn.com/problems/longest-increasing-subsequence/)

#### 2. 题目描述
给你一个整数数组 nums ，找到其中最长严格递增子序列的长度。

#### 3. 解题思路

* 动态规划：定义dp[i]为考虑前i个元素，以第i个数字结尾的最长上升子序列的长度

#### 4. 编码实现
``` java
public int lengthOfLIS(int[] nums) {
    if (nums == null || nums.length == 0) return 0;
    int[] dp = new int[nums.length];
    dp[0] = 0;
    int ans = 1;
    for (int i = 0; i < nums.length; i++) {
        dp[i] = 1;
        for (int j = 0; j < i; j++) {
            if (nums[i] > nums[j]) {
                dp[i] = Math.max(dp[i], dp[j] + 1);
            }
        }
        ans = Math.max(ans, dp[i]);
    }
    return ans;
}
```
