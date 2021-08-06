

#### 1. 题目链接
[数组中的第K个最大元素](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/)

#### 2. 题目描述
给定整数数组 nums 和整数 k，请返回数组中第 k 个最大的元素。

#### 3. 解题思路

* 使用快排

#### 4. 编码实现
``` java
public int findKthLargest(int[] nums, int k) {
    int len = nums.length;
    int left = 0, right = len - 1;
    int target = len - k;
    while (true) {
        int t = partition(nums, left, right);
        if (t == target) return nums[t];
        else if (t < target) left = t + 1;
        else right = t - 1;
    }
}

public int partition(int[] nums, int left, int right) {
    int pivot = nums[left];
    int j = left;
    for (int i = left + 1; i <= right; i++) {
        if (nums[i] < pivot) {
            swap(nums, ++j, i);
        }
    }
    swap(nums, j, left);
    return j;
}

public void swap(int[] nums, int i, int j) {
    int tmp = nums[i];
    nums[i] = nums[j];
    nums[j] = tmp;
}
```
