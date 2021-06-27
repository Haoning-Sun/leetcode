

#### 1. 题目链接 
[两数之和](https://leetcode-cn.com/problems/two-sum/)

#### 2. 题目描述
给定一个整数数组 nums和一个整数目标值 target，请你在该数组中找出 和为目标值 target 的那两个整数，并返回它们的数组下标。


#### 3. 解题思路
* 遍历数组
* 使用hash表记录键值对value和index(数值及其下标)
* 每次遍历数组得到数值nums[i]时，将target与nums[i]相减，判断结果是否在hash表中

#### 4. 编码实现
``` java
public int[] twoSum(int[] nums, int target) {
    Map<Integer,Integer> numMap = new HashMap();
    for(int i=0, length = nums.length; i < length; i++) {
        int tmp = target - nums[i];
        if(numMap.containsKey(tmp)) 
            return new int[]{numMap.get(tmp), i};
        numMap.put(nums[i], i);
    }
    return null;
}
```
