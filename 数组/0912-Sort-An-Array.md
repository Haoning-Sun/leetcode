

#### 1. 题目链接
[排序数组](https://leetcode-cn.com/problems/sort-an-array/)

#### 2. 题目描述
给你一个整数数组 nums，请你将该数组升序排列。

#### 3. 解题思路

* 快排

#### 4. 编码实现
``` java
public int[] sortArray(int[] nums) {
    quickSort(nums, 0, nums.length - 1);
    return nums;
}

public void quickSort(int[] nums, int left, int right) {
    if (left >= right) return;
    int partition = partition(nums, left, right);
    quickSort(nums, left, partition - 1);
    quickSort(nums, partition + 1, right);
}

public int partition(int[] nums, int left, int right) {
    int pivot = nums[left];
    while (left < right) {
        while (left < right && nums[right] >= pivot) right--;
        nums[left] = nums[right];
        while (left < right && nums[left] <= pivot) left++;
        nums[right] = nums[left];
    }
    nums[left] = pivot;
    return left;
}
```
