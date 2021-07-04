

#### 1. 题目链接
[2的幂](https://leetcode-cn.com/problems/power-of-two/)

#### 2. 题目描述
给你一个整数 n，请你判断该整数是否是 2 的幂次方。如果是，返回 true ；否则，返回 false

#### 3. 解题思路
* 2的幂必定大于0
* 2的幂的二进制表示只有1个1

#### 4. 编码实现
``` java
public boolean isPowerOfTwo(int n) {
    return n > 0 && (n & (n - 1)) == 0;
}
```
