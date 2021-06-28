

#### 1. 题目链接
[盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/)

#### 2. 题目描述
给你 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点(i,ai) 。在坐标内画 n 条垂直线，垂直线 i的两个端点分别为(i,ai) 和 (i, 0) 。找出其中的两条线，使得它们与x轴共同构成的容器可以容纳最多的水。

#### 3. 解题思路
* 思路一：枚举法
* 思路二：收缩法：用两个指针一个在头一个在尾，计算(i,j)容纳水的大小，然后将短的一侧向内部移动然后重新计算(i,j)更新最大值，直到两个指针相遇



#### 4. 编码实现
``` java
/**
 * 枚举法
 */
public int maxArea(int[] height) {
    int max = 0;
    for (int i = 0; i < height.length - 1; i++) {
        for (int j = i + 1; j < height.length; j++) {
            int area = (j - i) * Math.min(height[i], height[j]);
            max = Math.max(max, area);
        }
    }
    return max;
}
```

``` java
/**
 * 收缩法
 */
public int maxArea(int[] height) {
    int max = 0;
    for(int i = 0, j = height.length - 1; i < j;) {
        int minHeight = height[i] < height[j] ? height[i++] : height[j--];
        int area = (j - i + 1) * minHeight;
        max = Math.max(max, area);
    }
    return max;
}
```