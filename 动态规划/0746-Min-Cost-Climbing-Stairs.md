

#### 1. 题目链接
[使用最小花费爬楼梯](https://leetcode-cn.com/problems/min-cost-climbing-stairs/)

#### 2. 题目描述
数组的每个下标作为一个阶梯，第 i 个阶梯对应着一个非负数的体力花费值cost[i]（下标从 0 开始）。

每当你爬上一个阶梯你都要花费对应的体力值，一旦支付了相应的体力值，你就可以选择向上爬一个阶梯或者爬两个阶梯。

请你找出达到楼层顶部的最低花费。在开始时，你可以选择从下标为 0 或 1 的元素作为初始阶梯。

#### 3. 解题思路
* 动态规划:dp[i] = min(dp[i - 1], dp[i - 2]) + cost[i]

#### 4. 编码实现
``` java
public int minCostClimbingStairs(int[] cost) {
    int n = cost.length;
    int[] dp = new int[n];
    dp[0] = cost[0];
    dp[1] = cost[1];
    for (int i = 2; i < n; i++) {
        dp[i] = Math.min(dp[i - 1], dp[i - 2]) + cost[i];
    }
    return Math.min(dp[n - 1], dp[n - 2]);
    
    /**
    int dp0 = cost[0];
    int dp1 = cost[1];
    for (int i = 2; i < cost.length; i++) {
        int cur = Math.min(dp0, dp1) + cost[i];
        dp0 = dp1;
        dp1= cur;
    }
    return Math.min(dp0, dp1);
     */
}
```
