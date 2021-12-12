

#### 1. 题目链接
[下一个排列](https://leetcode-cn.com/problems/next-permutation/)

#### 2. 题目描述
实现获取 下一个排列 的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列（即，组合出下一个更大的整数）。

如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。

必须 原地 修改，只允许使用额外常数空间。

#### 3. 解题思路

* 从后向前查找第一个相邻升序的元素对 (i,j)，满足 A[i] < A[j]。此时 [j,end) 必然是降序
* 在 [j,end) 从后向前查找第一个满足 A[i] < A[k] 的 k。A[i]、A[k] 分别就是上文所说的「小数」、「大数」
* 将 A[i] 与 A[k] 交换
* 可以断定这时 [j,end) 必然是降序，逆置 [j,end)，使其升序
* 如果在步骤 1 找不到符合的相邻元素对，说明当前 [begin,end) 为一个降序顺序，则直接跳到步骤 4

#### 4. 编码实现
``` java
public void nextPermutation(int[] nums) {
    int i = nums.length - 2;
    while (i >=0 && nums[i] >= nums[i+1]) i--;
    if (i >= 0) {
        int j = nums.length - 1;
        while (j >= 0 && nums[i] >= nums[j]) j--;
        swap(nums, i, j);
    }
    reverse(nums, i + 1);
}

public void swap(int[] nums, int i, int j) {
    int tmp = nums[i];
    nums[i] = nums[j];
    nums[j] = tmp;
}

public void reverse(int[] nums, int start) {
    int left = start, right = nums.length - 1;
    while (left < right) {
        swap(nums, left, right);
        left++;
        right--;
    }
}

```
