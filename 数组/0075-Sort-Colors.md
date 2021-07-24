

#### 1. 题目链接
[跳跃游戏](https://leetcode-cn.com/problems/jump-game/)

#### 2. 题目描述
给定一个包含红色、白色和蓝色，一共n个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

此题中，我们使用整数 0、1和2分别表示红色、白色和蓝色。


#### 3. 解题思路

* 使用双指针，指针p0来交换0，p2来交换2，p0初始值为0，p2初始值为n-1；
* 找到2时，我们需要不断地将其与nums[p2]进行交换，直到新的nums[i]不为2，找到0时与其nums[p0]交换


#### 4. 编码实现
``` java
public void sortColors(int[] nums) {
    int p0 = 0, p2 = nums.length - 1;
    for (int i = 0; i <= p2; i++) {
        while (i <= p2 && nums[i] == 2) {
            swap(nums, i, p2--);
        }
        if (nums[i] == 0) {
            swap(nums, i, p0++);
        }
    }
}

public void swap(int[] nums, int n1, int n2) {
    int tmp = nums[n1];
    nums[n1] = nums[n2];
    nums[n2] = tmp;
}
```
