

#### 1. 题目链接
[反转字符串中的单词 III](https://leetcode-cn.com/problems/reverse-words-in-a-string-iii/)

#### 2. 题目描述
给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。

#### 3. 解题思路

* 遍历字符串，使用空格判断单词，然后依次翻转


#### 4. 编码实现
``` java
public String reverseWords(String s) {
    char[] str = s.toCharArray();
    int r = 0;
    for (int l = 0; l < str.length; l=r+1) {
        r = l;
        while (r < str.length && str[r] != ' ') { r++; }
        reverse(str, l, r - 1);
    }
    return new String(str);
}

public void reverse(char[] str, int l, int r) {
    while (l < r) {
        char c = str[l];
        str[l] = str[r];
        str[r] = c;
        l++;
        r--;
    }
}
```
