

#### 1. 题目链接
[位1的个数](https://leetcode-cn.com/problems/number-of-1-bits/)

#### 2. 题目描述
编写一个函数，输入是一个无符号整数（以二进制串的形式），返回其二进制表达式中数字位数为 '1' 的个数

#### 3. 解题思路
* n &= (n-1)会消除最末尾的1
* 统计上述计算的次数即可

#### 4. 编码实现
``` java
public int hammingWeight(int n) {
    int count = 0;
    while (n != 0) {
        count++;
        n &= (n-1);
    }
    return count;        
}
```
