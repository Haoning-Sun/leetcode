

#### 1. 题目链接
[删除有序数组中的重复项](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)

#### 2. 题目描述
给你一个有序数组 nums ，请你 原地 删除重复出现的元素，使每个元素 只出现一次 ，返回删除后数组的新长度。
不要使用额外的数组空间，你必须在 原地 修改输入数组 并在使用 O(1) 额外空间的条件下完成。



#### 3. 解题思路
* 数组排序
* 将其转换为target=a+b的问题
* 设置下标k从左开始遍历，target=0-nums[k]，且必须nums[k]<=0
* 设置双指针下标i,j初始值分别k+1和nums.length-1
* 使用夹逼的方法收缩指针判断是否有符合条件的解


#### 4. 编码实现
``` java
public int removeDuplicates(int[] nums) {
    if (nums == null || nums.length == 0) {
        return 0;
    }
    int k = 1;
    for (int i = 1; i < nums.length; i++) {
        if (nums[i] != nums[i-1]) {
            nums[k++] = nums[i];
        }
    }
    return k;
}
```
