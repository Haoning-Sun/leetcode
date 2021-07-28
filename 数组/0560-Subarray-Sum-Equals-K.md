
#### 1. 题目链接
[和为K的子数组](https://leetcode-cn.com/problems/subarray-sum-equals-k/)

#### 2. 题目描述
给定一个整数数组和一个整数k，你需要找到该数组中和为k的连续的子数组的个数。

#### 3. 解题思路

* 定义pre[i]为[0..i]里所有数的和，且有 pre[i]=pre[i−1]+nums[i]
* [j..i][j..i]这个子数组和为k这个条件我们可以转化为 pre[i]−pre[j−1]==k
* 从而有 pre[j−1]==pre[i]−k，即统计前缀和为pre[i]−k的pre[j]即可
* 使用hash表，键为和,值为出现次数

#### 4. 编码实现
``` java
public int subarraySum(int[] nums, int k) {
    Map<Integer, Integer> preSumMap = new HashMap<>();
    preSumMap.put(0, 1);
    int sum = 0;
    int count = 0;
    for (int i = 0; i < nums.length; i++) {
        sum += nums[i];
        if (preSumMap.containsKey(sum - k)) {
            count += preSumMap.get(sum - k);
        }
        preSumMap.put(sum, preSumMap.getOrDefault(sum, 0) + 1);
    }
    return count;
}
```
