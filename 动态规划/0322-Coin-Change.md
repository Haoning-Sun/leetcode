

#### 1. 题目链接
[零钱兑换](https://leetcode-cn.com/problems/coin-change/)

#### 2. 题目描述
给你一个整数数组 coins ，表示不同面额的硬币；以及一个整数 amount ，表示总金额。
计算并返回可以凑成总金额所需的 最少的硬币个数 。如果没有任何一种硬币组合能组成总金额，返回-1 。
你可以认为每种硬币的数量是无限的。


#### 3. 解题思路
* 动态规划，转移方程为 dp[money] = min(dp[money], dp[money - coins[coinIndex]] + 1)

#### 4. 编码实现
``` java
public int coinChange(int[] coins, int amount) {
    int max = amount + 1;
    int[] dp = new int[amount + 1];
    Arrays.fill(dp, max);
    dp[0] = 0;
    for (int i = 0; i < amount; i++) {
        for (int j = 0; j < coins.length; j++) {
            if (coins[j] <= i) {
                dp[i] = Math.min(dp[i], dp[i - coins[j]] + 1);
            }
        }
    }
    return dp[amount] > amount ? -1 : dp[amount];
}
```
