

#### 1. 题目链接
[不同路径](https://leetcode-cn.com/problems/unique-paths/)

#### 2. 题目描述
一个机器人位于一个 m x n网格的左上角 （起始点在下图中标记为 “Start” ）。
机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为 “Finish” ）。
问总共有多少条不同的路径？


#### 3. 解题思路
* 动态规划，dp[i][j]
* 对于第一行dp[0][j]，或者第一列 dp[i][0]，由于都是在边界，所以只能为1  
* dp[i][j] = dp[i-1][j] + dp[i][j-1]

#### 4. 编码实现
``` java
public int uniquePaths(int m, int n) {
    int[][] dp = new int[m][n];
    for (int i = 0; i < m; i++) {
        dp[i][0] = 1;
    }
    for (int j = 0; j < n; j++) {
        dp[0][j] = 1;
    }
    
    for (int i = 1; i < m; i++) {
        for (int j = 1; j < n; j++) {
            dp[i][j] = dp[i-1][j] + dp[i][j-1];
        }
    }
    return dp[m-1][n-1];
}
```
