

#### 1. 题目链接
[翻转字符串里的单词](https://leetcode-cn.com/problems/reverse-words-in-a-string/)

#### 2. 题目描述
给你一个字符串 s ，逐个翻转字符串中的所有 单词 。

单词 是由非空格字符组成的字符串。s 中使用至少一个空格将字符串中的 单词 分隔开。

请你返回一个翻转 s 中单词顺序并用单个空格相连的字符串。

#### 3. 解题思路

* 直接使用split


#### 4. 编码实现
``` java
public String reverseWords(String s) {
    String[] str = s.trim().split(" ");
    String res = new String("");
    for (int i = str.length - 1; i >= 0; i--) {
        if (!str[i].trim().equals("")) {
            res += (str[i] + " ");
        }
    }
    return res.trim();
}
```
