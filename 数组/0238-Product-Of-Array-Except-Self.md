
#### 1. 题目链接
[除自身以外数组的乘积](https://leetcode-cn.com/problems/product-of-array-except-self/)

#### 2. 题目描述
给你一个长度为n的整数数组nums，其中n > 1，返回输出数组output，其中 output[i]等于nums中除nums[i]之外其余各元素的乘积。


#### 3. 解题思路

* 初始化answer数组，对于给定索引i，answer[i]代表的是i左侧所有数字的乘积。
* 用一个遍历来跟踪右边元素的乘积。并更新数组answer[i]=answer[i]*R，R 更新为 R=R*nums[i]

#### 4. 编码实现
``` java
public int[] productExceptSelf(int[] nums) {
    int n = nums.length;
    int[] answers = new int[n];
    answers[0] = 1;
    for (int i = 1; i < n; i++) {
        answers[i] = answers[i-1]*nums[i-1];
    }
    int R = 1;
    for (int i = n - 1; i >= 0; i--) {
        answers[i] *= R;
        R *= nums[i];
    }
    return answers;
}
```
