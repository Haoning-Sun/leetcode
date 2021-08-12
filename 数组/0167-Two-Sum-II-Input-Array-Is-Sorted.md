

#### 1. 题目链接
[两数之和 II - 输入有序数组](https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/)

#### 2. 题目描述
给定一个已按照 升序排列  的整数数组 numbers ，请你从数组中找出两个数满足相加之和等于目标数 target


#### 3. 解题思路

* 双指针

#### 4. 编码实现
``` java
public int[] twoSum(int[] numbers, int target) {
    int start=0, end = numbers.length;
    while (start < end) {
        int sum = numbers[start] + numbers[end];
        if (sum == target) return new int[]{start+1, end+1};
        else if (sum > target) end--;
        else start++;
    }
    return null;
}
```
