

#### 1. 题目链接
[字符串相加](https://leetcode-cn.com/problems/add-strings/)

#### 2. 题目描述
给定两个字符串形式的非负整数 num1 和num2 ，计算它们的和并同样以字符串形式返回。

#### 3. 解题思路

* 设定 i，j 两指针分别指向 num1，num2 尾部，模拟人工加法
* carry用于计算进位
* 需注意当前索引是否溢出

#### 4. 编码实现
``` java
public String addStrings(String num1, String num2) {
    StringBuilder res = new StringBuilder("");
    int i = num1.length() - 1, j = num2.length() - 1, carry = 0;
    while (i >=0 || j >= 0) {
        int n1 = i >= 0 ? num1.charAt(i) - '0' : 0;
        int n2 = j >= 0 ? num2.charAt(j) - '0' : 0;
        int tmp = n1 + n2 + carry;
        carry = tmp/10;
        res.append((tmp%10));
        i--;j--;
    }
    if (carry > 0) res.append("1");
    return res.reverse().toString();
}
```
