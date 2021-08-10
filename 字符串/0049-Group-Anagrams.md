

#### 1. 题目链接
[字母异位词分组](https://leetcode-cn.com/problems/group-anagrams/)

#### 2. 题目描述
给你一个字符串数组，请你将 字母异位词 组合在一起。可以按任意顺序返回结果列表。

#### 3. 解题思路

* 排序后使用map存储

#### 4. 编码实现
``` java
public List<List<String>> groupAnagrams(String[] strs) {
    Map<String, List<String>> map = new HashMap<String, List<String>>();
    for (String str : strs) {
        char[] array = str.toCharArray();
        Arrays.sort(array);
        String key = new String(array);
        List<String> list = map.getOrDefault(key, new ArrayList<String>());
        list.add(str);
        map.put(key, list);
    }
    return new ArrayList<List<String>>(map.values());
}
```
