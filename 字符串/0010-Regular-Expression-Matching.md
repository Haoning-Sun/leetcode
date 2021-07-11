

#### 1. 题目链接
[正则表达式匹配](https://leetcode-cn.com/problems/regular-expression-matching/)

#### 2. 题目描述
给你一个字符串s和一个字符规律p，请你来实现一个支持 '.'和'*'的正则表达式匹配。

'.' 匹配任意单个字符
'*' 匹配零个或多个前面的那一个元素
所谓匹配，是要涵盖整个字符串s的，而不是部分字符串。

#### 3. 解题思路

* 动态规划
* s和p倒着看，dp[i][j]dp[i][j]的取值分为以下几种情况：
    * p[j−1]为普通字符,若s[i-1] == p[j-1]，则dp[i][j]=dp[i−1][j−1]，否则匹配失败
    * p[j−1]为'.'，则dp[i][j]=dp[i−1][j−1]
    * p[j−1]为'*'：
        * 匹配1次，相当于去掉s的第一个字符，继续向后匹配，则dp[i][j]=dp[i][j−2]
        * 不进行匹配，相当于s不变，p向后去掉两位，则dp[i][j]=dp[i−1][j]
        
    


#### 4. 编码实现
``` java
public boolean isMatch(String s, String p) {
    char[] str = s.toCharArray();
    char[] ptr = p.toCharArray();
    int slen = str.length;
    int plen = ptr.length;
    boolean[][] dp = new boolean[slen+1][plen+1];
    dp[0][0] = true;
    for (int i = 0; i <= slen; i++) {
        for (int j = 1; j <= plen; j++) {
            if (ptr[j-1] != '*') {
                if (i > 0 && (str[i-1] == ptr[j-1] || ptr[j-1] == '.')) {
                    dp[i][j] = dp[i-1][j-1];
                } 
            } else {
                if (j > 1) dp[i][j] |= dp[i][j-2];
                if (i > 0 && j > 1 && (str[i-1] == ptr[j-2] || ptr[j-2] == '.')) dp[i][j] |= dp[i-1][j];
            }
        }
    }
    return dp[slen][plen];
}
```
