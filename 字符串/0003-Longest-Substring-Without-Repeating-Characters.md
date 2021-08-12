

#### 1. 题目链接
[无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

#### 2. 题目描述
给定一个字符串s，请你找出其中不含有重复字符的 最长子串 的长度。


#### 3. 解题思路

* 使用滑动窗口，遍历每个字符  
* 使用set记录此时已遍历过的字符
* 发现重复字符时，根据子串长度计算最大长度

#### 4. 编码实现
``` java
public int lengthOfLongestSubstring(String s) {
    int n = s.length();
    Set<Character> occ = new HashSet<>();
    int rk = -1, ans = 0;
    for (int i = 0; i < n; i++) {
        if (i != 0) {
            occ.remove(s.charAt(i - 1));
        }
        while (rk + 1 < n && !occ.contains(s.charAt(rk + 1))) {
            occ.add(s.charAt(rk + 1));
            rk++;
        }
        ans = Math.max(ans, rk - i + 1);
    }
    return ans;
}

/**
  双指针法
 */
public int lengthOfLongestSubstring(String s) {
    int n = s.length();
    Map<Character, Integer> map = new HashMap<>();
    int max = 0;
    int start = 0;
    char[] sc = s.toCharArray();
    for (int i = 0; i < n; i++) {
        if (map.contains[sc[i]]) {
            start = Math.max(map.get(sc[i]), start);
        }
        max = Math.max(max, i - start + 1);
        map.put(sc[i], i + 1);
    }
    return max;
}
```
