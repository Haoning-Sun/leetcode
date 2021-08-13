

#### 1. 题目链接
[打家劫舍 II](https://leetcode-cn.com/problems/house-robber-ii/)

#### 2. 题目描述
你是一个专业的小偷，计划偷窃沿街的房屋，每间房内都藏有一定的现金。这个地方所有的房屋都 围成一圈 ，这意味着第一个房屋和最后一个房屋是紧挨着的。同时，相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警

#### 3. 解题思路

* 如果不偷窃最后一间房屋，则偷窃房屋的下标范围是 [0,n-2]；如果不偷窃第一间房屋，则偷窃房屋的下标范围是 [1,n-1]
* 然后使用打家劫舍的动态规划方法解决

#### 4. 编码实现
``` java
public int rob(int[] nums) {
    int n = nums.length;
    if (n == 1) return nums[0];
    if (n == 2) return Math.max(nums[0], nums[1]);
    return Math.max(rob(nums, 0, n-2), rob(nums, 1, n-1));
}

public int rob(int[] nums, int start, int end) {
    int pre2 = 0, pre1 = 0;
    for (int i = start; i <= end; i++) {
        int cur = Math.max(pre2 + nums[i], pre1);
        pre2 = pre1;
        pre1 = cur;
    }
    return pre1;
}
```
