

#### 1. 题目链接
[最长公共前缀](https://leetcode-cn.com/problems/longest-common-prefix/)

#### 2. 题目描述
编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。


#### 3. 解题思路

* 纵向扫描，依次遍历所有字符串的每一列进行对比


#### 4. 编码实现
``` java
public String longestCommonPrefix(String[] strs) {
    if (strs == null || strs.length == 0) return "";
    
    int length = strs[0].length();
    int count = strs.length;
    
    for (int i = 0; i < length; i++) {
        char c = strs[0].charAt(i);
        for (int j = 1; j < count; j++) {
            if (i == strs[j].length() || strs[j].charAt(i) != c) {
                return strs[0].substring(0, i);
            }
        }
    }
    return strs[0];
}
```
