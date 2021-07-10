

#### 1. 题目链接
[反转字符串](https://leetcode-cn.com/problems/reverse-string/)

#### 2. 题目描述
编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组 char[] 的形式给出。

不要给另外的数组分配额外的空间，你必须原地修改输入数组、使用 O(1) 的额外空间解决这一问题。

#### 3. 解题思路

* 使用双指针


#### 4. 编码实现
``` java
public void reverseString(char[] s) {
    if (s == null || s.length < 2) return;
    
    int i = 0;
    int j = s.length - 1;
    while (i < j) {
        char c = s[i];
        s[i] = s[j];
        s[j] = c;
        i++;
        j--;
    }
}
```
