

#### 1. 题目链接
[只出现一次的数字](https://leetcode-cn.com/problems/single-number/)

#### 2. 题目描述
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

#### 3. 解题思路

* 如果不偷窃最后一间房屋，则偷窃房屋的下标范围是 [0,n-2]；如果不偷窃第一间房屋，则偷窃房屋的下标范围是 [1,n-1]
* 然后使用打家劫舍的动态规划方法解决

#### 4. 编码实现
``` java
public int singleNumber(int[] nums) {
    int ans = 0;
    for (int num : nums) {
        ans ^= num;
    }
    return ans;
}
```
