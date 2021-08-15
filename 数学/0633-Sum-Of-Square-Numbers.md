

#### 1. 题目链接
[方数之和](https://leetcode-cn.com/problems/sum-of-square-numbers/)

#### 2. 题目描述
给定一个非负整数c，你要判断是否存在两个整数 a 和 b，使得a^2 + b^2 = c

#### 3. 解题思路



#### 4. 编码实现
``` java
public boolean judgeSquareSum(int c) {
    if (c < 0) return false;
    int i = 0, j = Math.sqrt(c);
    while (i <= j) {
        int sum = i*i + j*j;
        if (sum == c) return true;
        else if (sum < c) i++;
        else j--;
    }
    return false;
}
```
