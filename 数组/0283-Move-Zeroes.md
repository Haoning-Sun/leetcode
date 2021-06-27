

#### 1. 题目链接
[移动零](https://leetcode-cn.com/problems/move-zeroes/)

#### 2. 题目描述
给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。


#### 3. 解题思路
##### 3.1 思路
* 遍历数组
* 使用一个变量j记录位置，将不为0的元素依次复制到nums的前面
* j不等于原位置则将原位置元素设置为0（或者：每次交换j和i位置元素，有1) j<=i; 2)每次nums[j]约nums[i]交换时，要么i==j，要么nums[j]=0）


#### 4. 编码实现
``` java
public void moveZeroes(int[] nums) {
    int j = 0;
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != 0) {
            nums[j] = nums[i];
            if (i != j) {
                nums[i] = 0;
            }
            j++;
        }
    }
}
```

``` java
public void moveZeroes(int[] nums) {
    int j = 0;
    for (int i = 0; i < nums.length; i++) {
        //swap
        if (nums[i] != 0) {
            int tmp = nums[j];
            nums[j] = nums[i];
            nums[i] = tmp;
            j++;
        }
    }
}
```
