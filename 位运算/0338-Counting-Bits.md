
#### 1. 题目链接
[比特位计数](https://leetcode-cn.com/problems/counting-bits/)

#### 2. 题目描述
给定一个非负整数 num。对于 0 ≤ i ≤ num 范围中的每个数字 i ，计算其二进制数中的 1 的数目并将它们作为数组返回。


#### 3. 解题思路

* 对于正整数 xx，将其二进制表示右移一位，等价于将其二进制表示的最低位去掉，得到的数是x/2，如果bits[x/2]已知，则：
    * x为偶数，bits[x] = bits[x/2]
    * x为奇数，bits[x] = bits[x/2] + 1
    
#### 4. 编码实现
``` java
public int[] countBits(int n) {
    int[] bits = new int[n+1];
    for (int  i = 1; i <= n; i++) {
        bits[i] = bits[i>>1] + (i&1);
    }
    return bits;
}
```
