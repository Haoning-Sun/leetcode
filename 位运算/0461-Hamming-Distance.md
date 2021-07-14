

#### 1. 题目链接
[汉明距离](https://leetcode-cn.com/problems/hamming-distance/)

#### 2. 题目描述
两个整数之间的 汉明距离 指的是这两个数字对应二进制位不同的位置的数目。
给你两个整数 x 和 y，计算并返回它们之间的汉明距离。

#### 3. 解题思路
* 两个数异或然后统计结果中等于1的位数

#### 4. 编码实现
``` java
public int hammingDistance(int x, int y) {
    int s = x ^ y;
    int count = 0;
    while (s != 0) {
        count += s&1;
        s >>= 1;
    }
    return count;
}
```
