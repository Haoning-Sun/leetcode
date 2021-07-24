

#### 1. 题目链接
[子集](https://leetcode-cn.com/problems/subsets/)

#### 2. 题目描述
给你一个整数数组 nums ，数组中的元素 互不相同 。返回该数组所有可能的子集（幂集）。


#### 3. 解题思路
* 使用递归和回溯的方式来列举，每次需要考虑取获取不取当前元素

#### 4. 编码实现
``` java
List<Integer> t = new ArrayList<>();
List<List<Integer>> ans = new ArrayList<>();
public List<List<Integer>> subsets(int[] nums) {
    dfs(0, nums);
    return ans;
}

public void dfs(int cur, int[] nums) {
    if (cur == nums.length) {
        ans.add(new ArrayList<>(t));
        return;
    }
    t.add(nums[cur]);
    dfs(cur + 1, nums);
    t.remove(t.size() - 1);
    dfs(cur + 1, nums);
}
```
