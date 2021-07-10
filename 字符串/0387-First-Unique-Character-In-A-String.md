

#### 1. 题目链接
[字符串中的第一个唯一字符](https://leetcode-cn.com/problems/first-unique-character-in-a-string/)

#### 2. 题目描述
给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。

#### 3. 解题思路
* 遍历字符串，使用map数组保存每个字符是否唯一，第一次存入为true，再碰到则修改为false
* 遍历字符串，返回map中第一个为true的下标



#### 4. 编码实现
``` java
public int firstUniqChar(String s) {
    Map<Character, Boolean> map = new LinkedHashMap<Character, Boolean>();
    for (char c : s.toCharArray()) {
        if (map.containsKey(c)) {
            map.put(c, false);
        } else {
            map.put(c, true);
        }
    }
    for (int i = 0; i < s.length(); i++) { 
        if (map.get(s.charAt(i))) {
            return i;
        }
    }
    return -1;
}
```
