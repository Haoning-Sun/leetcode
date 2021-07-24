

#### 1. 题目链接
[最大正方形](https://leetcode-cn.com/problems/maximal-square/)

#### 2. 题目描述
在一个由 '0' 和 '1' 组成的二维矩阵内，找到只包含 '1' 的最大正方形，并返回其面积。

#### 3. 解题思路
* 动态规划，用dp[i][j]表示以(i,j)为右下角，且只包含1的正方形的边长最大值
* 如果matrix[i][j]为0，则dp[i][j]=0；如果为1，则dp[i][j]=min(dp[i-1][j-1],dp[i][j-1],dp[i-1][j])+1

#### 4. 编码实现
``` java
public int maximalSquare(char[][] matrix) {
    if (matrix == null || matrix.length == 0 || matrix[0].length == 0) return 0;
    int row = matrix.length, column = matrix[0].length;
    int[][] dp = new int[row][column];
    int maxSide = 0;
    for (int i = 0; i < row; i++) {
        for (int j = 0; j < column; j++) {
            if (matrix[i][j] == '1') {
                if (i == 0 || j == 0) {
                    dp[i][j] = 1;
                } else {
                    dp[i][j] = Math.min(Math.min(dp[i-1][j], dp[i][j-1]), dp[i-1][j-1]) + 1;
                }
                maxSide = Math.max(dp[i][j], maxSide);
            }
        }
    }
    int maxSequart = maxSide * maxSide;
    return maxSequart;
}
```
