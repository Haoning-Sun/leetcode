

#### 1. 题目链接
[乘积最大子数组](https://leetcode-cn.com/problems/maximum-product-subarray/)

#### 2. 题目描述
给你一个整数数组 nums ，请你找出数组中乘积最大的连续子数组（该子数组中至少包含一个数字），并返回该子数组所对应的乘积。

#### 3. 解题思路
* 动态规划
* 因为负负得正，所以需要保存最小值
* max = max(max * nums[i], nums[i])
* min = min(min * nums[i], nums[i])
* nums[i]为负数时需要交换min和max再继续计算

#### 4. 编码实现
``` java
public int maxProduct(int[] nums) {
    int max = nums[0], imax = nums[0], imin = nums[0];
    for (int i = 1; i < nums.length; i++) {
        if (nums[i] < 0) {
            int tmp = imax;
            imax = imin;
            imin = tmp;
        }
        imax = Math.max(nums[i] * imax, nums[i]);
        imin = Math.min(nums[i] * imin, nums[i]);
        max = Math.max(max, imax);
    }
    return max;
}
```
