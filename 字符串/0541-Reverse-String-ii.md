

#### 1. 题目链接
[反转字符串 II](https://leetcode-cn.com/problems/reverse-string-ii/)

#### 2. 题目描述
给定一个字符串 s 和一个整数 k，你需要对从字符串开头算起的每隔2k 个字符的前 k 个字符进行反转。
如果剩余字符少于 k 个，则将剩余字符全部反转。
如果剩余字符小于 2k 但大于或等于 k 个，则反转前 k 个字符，其余字符保持原样。

#### 3. 解题思路

* 使用双指针


#### 4. 编码实现
``` java
public String reverseStr(String s, int k) {
    if (s == null || s.length() < 2) return s;
    int len = s.length();
    char[] str = s.toCharArray();
    
    for (int i = 0; i < len; i += (2*k)) {
        int l = i, r = Math.min(l + k - 1, len - 1);
        reverse(str, l ,r);
    }
    return new String(str);
}

public void reverse(char[] str, int l, int r) {
    while (l < r) {
        char tmp = str[l];
        str[l] = str[r];
        str[r] = tmp;
        l++;
        r--;
    }
}
```
