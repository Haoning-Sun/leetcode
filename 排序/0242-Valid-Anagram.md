

#### 1. 题目链接
[有效的字母异位词](https://leetcode-cn.com/problems/valid-anagram/)

#### 2. 题目描述
给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的字母异位词。

#### 3. 解题思路
* 排序后判断是否相等

#### 4. 编码实现
``` java
public boolean isAnagram(String s, String t) {
    char[] str1 = s.toCharArray();
    char[] str2 = t.toCharArray();
    Arrays.sort(str1);
    Arrays.sort(str2);
    return Arrays.equals(str1, str2);  
}
```
