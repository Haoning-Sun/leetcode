

#### 1. 题目链接
[字符串中的第一个唯一字符](https://leetcode-cn.com/problems/first-unique-character-in-a-string/)

#### 2. 题目描述
给定字符串J代表石头中宝石的类型，和字符串S代表你拥有的石头。S中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。
J中的字母不重复，J和S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。

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
