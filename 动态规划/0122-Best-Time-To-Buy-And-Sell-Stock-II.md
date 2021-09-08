

#### 1. 题目链接
[买卖股票的最佳时机 II](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/)

#### 2. 题目描述
给定一个数组 prices ，其中prices[i] 是一支给定股票第 i 天的价格。
设计一个算法来计算你所能获取的最大利润。你可以尽可能地完成更多的交易（多次买卖一支股票）。


#### 3. 解题思路
* 定义状态dp[i][0] 表示第i天交易完后手里没有股票的最大利润，dp[i][1] 表示第i天交易完后手里持有一支股票的最大利润
* dp[i][0]=max{dp[i−1][0],dp[i−1][1]+prices[i]}
* dp[i][1]=max{dp[i−1][1],dp[i−1][0]−prices[i]}

#### 4. 编码实现
``` java
public int maxProfit(int[] prices) {
    int n = prices.length;
    int[][] dp = new int[n][2];
    dp[0][1] = -prices[0];
    for (int i = 1; i < n; i++) {
        dp[i][0] = Math.max(dp[i-1][0], dp[i-1][1] + prices[i]);
        dp[i][1] = Math.max(dp[i-1][1], dp[i-1][0] - prices[i]);
    }
    return dp[n-1][0];
}
```
