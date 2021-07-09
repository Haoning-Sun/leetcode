
#### 1. 题目链接
[Pow(x, n)](https://leetcode-cn.com/problems/powx-n/)

#### 2. 题目描述
实现 pow(x, n) ，即计算 x 的 n 次幂函数（即，xn）。


#### 3. 解题思路
* 迭代

#### 4. 编码实现
``` java
public double myPow(double x, int n) {
    long N = n;
    return N > 0 ? quickMul(x, N) : 1.0 / quickMul(x, -N);
}

public double quickMul(double x, long N) {
    double ans = 1.0;
    double x_contribute = x;
    while (N > 0) {
        if (N % 2 == 1) {
            ans *= x_contribute;
        }
        x_contribute *= x_contribute;
        N /= 2; 
    }
    return ans;
}
```
