

#### 1. 题目链接
[最后一个单词的长度](https://leetcode-cn.com/problems/length-of-last-word/)

#### 2. 题目描述
给你一个字符串 s，由若干单词组成，单词之间用空格隔开。返回字符串中最后一个单词的长度。如果不存在最后一个单词，请返回 0 。

单词 是指仅由字母组成、不包含任何空格字符的最大子字符串。

#### 3. 解题思路
* 去掉首尾空格
* 从后往前遍历，遇到空格停止，否则count++
* 返回count



#### 4. 编码实现
``` java
public int lengthOfLastWord(String s) {
    int count = 0;
    s = s.trim();
    for (int i = s.length() - 1; i >= 0; i--) {
        if (s.charAt(i) == ' ') break;
        else count++;
    }
    return count;
}
```
