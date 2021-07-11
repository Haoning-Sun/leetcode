

#### 1. 题目链接
[最长回文子串](https://leetcode-cn.com/problems/longest-palindromic-substring/)

#### 2. 题目描述
给你一个字符串 s，找到 s 中最长的回文子串。

#### 3. 解题思路
* 动态规划
* 定义dp[i][j]
  * s[i,j]是回文串则dp[i][j]=true，否则dp[i][j]=false
  * dp[i][j] = dp[i-1][j-1] && s[i]==s[j]

#### 4. 编码实现
``` java
public String longestPalindrome(String s) {
    int n = s.length();
    String ans = "";
    boolean[][] dp = new boolean[n][n];
    
    for (int i = n - 1; i >= 0; i--) {
        for (int j = i; j < n; j++) {
            dp[i][j] = s.charAt(i) == s.charAt(j) && (j - i < 2 || dp[i+1][j-1]);
            if (dp[i][j] && j - i + 1 > ans.length()) {
                ans = s.substring(i, j + 1);
            }
        }
    }
    return ans;
}
```
