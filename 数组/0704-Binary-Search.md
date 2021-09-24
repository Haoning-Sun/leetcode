

#### 1. 题目链接
[二分查找](https://leetcode-cn.com/problems/binary-search/)

#### 2. 题目描述
给定一个n个元素有序的（升序）整型数组nums和一个目标值target，写一个函数搜索nums中的 target，如果目标值存在返回下标，否则返回 -1。

#### 3. 解题思路

* 折半查找

#### 4. 编码实现
``` java
public int search(int[] nums, int target) {
    int left = 0, right = nums.length - 1;
    while (left <= right) {
        int mid = (left + right) >> 1;
        if (nums[mid] == target) return mid;
        else if (nums[mid] < target) left = mid + 1;
        else right = mid - 1;
    }        
    return -1;
}
```
