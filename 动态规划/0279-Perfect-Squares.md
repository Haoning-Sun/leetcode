
#### 1. 题目链接
[完全平方数](https://leetcode-cn.com/problems/perfect-squares/)

#### 2. 题目描述
给定正整数n，找到若干个完全平方数（比如1, 4, 9, 16, ...）使得它们的和等于 n。你需要让组成和的完全平方数的个数最少。

给你一个整数 n ，返回和为 n 的完全平方数的 最少数量。

#### 3. 解题思路

* 动态规划：dp[i] = MIN(dp[i], dp[i - j * j] + 1)

#### 4. 编码实现
``` java
public int numSquares(int n) {
    int[] f = new int[n+1];
    for (int i = 1; i <= n; i++) {
        int minn = Integer.MAX_VALUE;
        for (int j = 1; j*j <= i; j++) {
            minn = Math.min(minn, f[i-j*j]);
        }
        f[i] = minn + 1;
    }
    return f[n];
}
```
