

#### 1. 题目链接
[最长重复子数组](https://leetcode-cn.com/problems/maximum-length-of-repeated-subarray/)

#### 2. 题目描述
给两个整数数组 A 和 B ，返回两个数组中公共的、长度最长的子数组的长度。

#### 3. 解题思路

* 动态规划：令 dp[i][j] 表示 A[i:] 和 B[j:] 的最长公共前缀，那么答案即为所有 dp[i][j] 中的最大值。如果 A[i] == B[j]，那么 dp[i][j] = dp[i + 1][j + 1] + 1，否则 dp[i][j] = 0

#### 4. 编码实现
``` java
public int findLength(int[] nums1, int[] nums2) {
    int m = nums1.length, n = nums2.length;
    int[][] dp = new int[m+1][n+1];
    int ans = 0;
    for (int i = m-1; i >= 0; i--) {
        for (int j = n-1; j >= 0; j--) {
            dp[i][j] = nums1[i] == nums2[j] ? dp[i+1][j+1]+1 : 0;
            ans = Math.max(ans, dp[i][j]);
        }
    }
    return ans;
}
```
