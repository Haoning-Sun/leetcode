

#### 1. 题目链接
[方数之和](https://leetcode-cn.com/problems/sum-of-square-numbers/)

#### 2. 题目描述
给定一个非负整数c，你要判断是否存在两个整数 a 和 b，使得a^2 + b^2 = c

#### 3. 解题思路

* 使用双指针

#### 4. 编码实现
``` java
public void merge(int[] nums1, int m, int[] nums2, int n) {
    int i = m - 1, j = n - 1, k = m + n - 1;
    while (i >= 0 && j >= 0) {
        if (nums1[i] > nums2[j]) {
            nums1[k--] = nums1[i--];
        } else {
            nums1[k--] = nums2[j--];
        }
    }
    while (j >= 0) {
        nums1[k--] = nums2[j--];
    }
}
```
