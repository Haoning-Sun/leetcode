

#### 1. 题目链接
[三数之和](https://leetcode-cn.com/problems/move-zeroes/)

#### 2. 题目描述
给你一个包含 n 个整数的数组nums，判断nums中是否存在三个元素 a，b，c ，使得a + b + c = 0 ？请你找出所有和为 0 且不重复的三元组。

注意：答案中不可以包含重复的三元组。


#### 3. 解题思路
* 数组排序
* 将其转换为target=a+b的问题  
* 设置下标k从左开始遍历，target=0-nums[k]，且必须nums[k]<=0 
* 设置双指针下标i,j初始值分别k+1和nums.length-1
* 使用夹逼的方法收缩指针判断是否有符合条件的解


#### 4. 编码实现
``` java
public List<List<Integer>> threeSum(int[] nums) {
    Arrays.sort(nums);
    List<List<Integer>> result = new ArrayList<>();
    if(nums == null || nums.length < 3) return result;
    for (int i = 0; i < nums.length - 2; i++) {
        if(nums[i] > 0) break;
        if(i > 0 && nums[i] == nums[i - 1]) continue;
        int lo = i + 1, hi = nums.length - 1, sum = 0 - nums[i];
        while (lo < hi) {
            if (nums[lo] + nums[hi] == sum) {
                result.add(Arrays.asList(nums[i], nums[lo], nums[hi]));
                while (lo < hi && nums[lo] == nums[lo+1]) lo++;
                while (lo < hi && nums[hi] == nums[hi-1]) hi--;
                lo++; hi--;
            } else if (nums[lo] + nums[hi] < sum) { 
                lo++;
            } else {
                hi--;
            }
        }
    }
    return result;
}
```
