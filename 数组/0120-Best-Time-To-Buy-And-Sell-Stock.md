

#### 1. 题目链接
[买卖股票的最佳时机](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/)

#### 2. 题目描述
给定一个数组 prices ，它的第i 个元素prices[i] 表示一支给定股票第 i 天的价格。
你只能选择 某一天 买入这只股票，并选择在 未来的某一个不同的日子 卖出该股票。设计一个算法来计算你所能获取的最大利润。
返回你可以从这笔交易中获取的最大利润。如果你不能获取任何利润，返回 0 。

#### 3. 解题思路
* 使用两个变量分别保存最小股价和最大价值
* 遍历prices数组，计算比较最小股价和最大价值，进行更新

#### 4. 编码实现
``` java
public int maxProfit(int[] prices) {
    int minPrice = Integer.MAX_VALUE;
    int maxProfit = 0;
    for (int i = 0; i < prices.length; i++) {
        if (minPrice > prices[i]) minPrice = prices[i];
        if (prices[i] > minPrice) maxProfit = Math.max(maxProfit, prices[i] - minPrice);
    }
    return maxProfit;
}
```
