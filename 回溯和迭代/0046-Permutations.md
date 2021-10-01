

#### 1. 题目链接
[全排列](https://leetcode-cn.com/problems/permutations/)

#### 2. 题目描述
给定一个不含重复数字的数组 nums ，返回其 所有可能的全排列 。你可以 按任意顺序 返回答案。

#### 3. 解题思路

* 使用深度优先遍历和回溯法

#### 4. 编码实现
``` java
List<List<Integer>> result = new ArrayList<>();
public List<List<Integer>> permute(int[] nums) {
    int len = nums.length;
    if (len == 0) return result;
    boolean[] used = new boolean[len];
    List<Integer> path = new ArrayList<>();
    dfs(nums, len, 0, used, path);    
}

public void dfs(int[] nums, int len, int depth, boolean[] used, List<Integer> path) {
    if (depth == len) {
        result.add(path);
    }
    
    for (int i = 0; i < len; i++) {
        if (!used[i]) {
            path.add(nums[i]);
            used[i] = true;
            dfs(nums, len, depth + 1, used, path);
            used[i] = false;
            path.remove(path.size() - 1);
        }
    }
}
```
