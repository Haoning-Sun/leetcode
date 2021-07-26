

#### 1. 题目链接
[接雨水](https://leetcode-cn.com/problems/trapping-rain-water/)

#### 2. 题目描述
给定n个非负整数表示每个宽度为1的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。

#### 3. 解题思路
* 维护两个指针left和right以及两个变量leftMax和rightMax，初始时left=0,right=n-1,leftMax=0,rightMax=0。left只会向右移动,right只会向左移动，在移动指针的过程中更新两个变量leftMax和rightMax的值
* 指针移动后计算height[left]和height[right]中相对低的一方的容量
* 当前位置能够接水的容量则有当前位置高度height[left]/height[right]与其对应的leftMax/rightMax决定

#### 4. 编码实现
``` java
public int trap(int[] height) {
    int left = 0, right = height.length - 1;
    int leftMax = 0, rightMax = 0;
    int ans = 0;
    while (left < right) {
        if (height[left] < height[right]) {
            leftMax = Math.max(leftMax, height[left]);
            ans += (leftMax - height[left]);
            left++;
        } else {
            rightMax = Math.max(rightMax, height[right]);
            ans += (rightMax - height[right]);
            right--;
        }
    }
    return ans;
}
```
