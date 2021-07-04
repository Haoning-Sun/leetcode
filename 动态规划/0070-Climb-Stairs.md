

#### 1. 题目链接
[爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)

#### 2. 题目描述
假设你正在爬楼梯。需要 n 阶你才能到达楼顶。
每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

#### 3. 解题思路
* 思路一：递归法
* 思路二：动态规划：dp[n] = dp[n-1] + dp[n-2]

#### 4. 编码实现
``` java
/**
 * 递归法
 */
public int climbStairs(int n) {
    if(n <= 2) {
        return n;
    }
    return climbStairs(n-1) + climbStairs(n-2);
}
```

``` java
/**
 * 动态规划
 */
 public int climbStairs(int n) {
    if(n <= 2) {
        return n;
    }
    int f1 = 1;
    int f2 = 2;
    int f3 = 3;
    for(int i = 3; i <= n; i++) {
        f3 = f2 + f1;
        f1 = f2;
        f2 = f3;
    }
    return f3;
}
```