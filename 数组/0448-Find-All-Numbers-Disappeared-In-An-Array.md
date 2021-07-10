
#### 1. 题目链接
[找到所有数组中消失的数字](https://leetcode-cn.com/problems/find-all-numbers-disappeared-in-an-array/)

#### 2. 题目描述
给你一个含 n 个整数的数组 nums ，其中 nums[i] 在区间 [1, n] 内。请你找出所有在 [1, n] 范围内但没有出现在 nums 中的数字，并以数组的形式返回结果。



#### 3. 解题思路
* 遍历nums，每遇到一个数x，就让nums[x−1]增加n。由于nums中所有数均在 [1,n][1,n] 中，增加以后，这些数必然大于n。最后我们遍历nums，若nums[i] 未大于n，就说明没有遇到过数i+1。这样我们就找到了缺失的数字。


#### 4. 编码实现
``` java
public List<Integer> findDisappearedNumbers(int[] nums) {
    int n = nums.length;
    for (int num : nums) {
        int x = (num - 1) % n;
        nums[x] += n;
    } 
    List<Integer> ret = new ArrayList<>();
    for (int i = 0; i < n; i++) {
        if (nums[i] <= n) 
            ret.add(i + 1);
    }
    return ret;
}
```
