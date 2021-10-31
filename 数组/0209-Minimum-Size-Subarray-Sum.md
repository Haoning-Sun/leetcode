

#### 1. 题目链接
[长度最小的子数组](https://leetcode-cn.com/problems/minimum-size-subarray-sum/)

#### 2. 题目描述
给定一个含有n个正整数的数组和一个正整数 target 。

找出该数组中满足其和 ≥ target 的长度最小的 连续子数组[numsl, numsl+1, ..., numsr-1, numsr] ，并返回其长度。如果不存在符合条件的子数组，返回0。

#### 3. 解题思路

* 定义两个指针start和end分别表示子数组（滑动窗口窗口）的开始位置和结束位置，维护变量sum存储子数组中的元素和
* 初始状态下，start和end都指向下标0，sum的值为0
* 每一轮迭代，将nums[end]加到sum，如果sum≥s，则更新子数组的最小长度（此时子数组的长度是end−start+1），然后将nums[start] 从sum中减去并将start右移，直到sum < s，在此过程中同样更新子数组的最小长度。在每一轮迭代的最后，将end右移。

#### 4. 编码实现
``` java
public int minSubArrayLen(int target, int[] nums) {
    if (nums == null || nums.length == 0) return 0;
    int start = 0, end = 0, len = nums.length;
    int ans = Integer.MAX_VALUE;
    int sum = 0;
    while (end < len) {
        sum += nums[end];
        while (sum >= target) {
           ans = Math.min(ans, end - start + 1);
           sum -= nums[start];
           start++;
        }
        end++;
    } 
    return ans == Integer.MAX_VALUE ? 0 : ans;
}
```
