

#### 1. 题目链接
[多数元素](https://leetcode-cn.com/problems/majority-element/)

#### 2. 题目描述
给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数 大于 ⌊ n/2 ⌋ 的元素。


#### 3. 解题思路
* 使用递归和回溯的方式来列举，每次需要考虑取获取不取当前元素

#### 4. 编码实现
``` java
public int majorityElement(int[] nums) {
    int count = 0;
    int candidate = 0;
    for (int num : nums) {
        if (count == 0) {
            candidate = num;
        }
        count += (candidate == num ? 1 : -1);
    }
    return candidate;
}
```
