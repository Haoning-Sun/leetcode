

#### 1. 题目链接
[加一](https://leetcode-cn.com/problems/plus-one/)

#### 2. 题目描述
给定一个由 整数 组成的 非空 数组所表示的非负整数，在该数的基础上加一。
最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。
你可以假设除了整数 0 之外，这个整数不会以零开头。

#### 3. 解题思路
* 元素为9加1才会进位，加1后原位置元素变为0
* 碰到不进位的位置则无需继续
* 若进位到最高位加1，其余为肯定均为0

#### 4. 编码实现
``` java
public int[] plusOne(int[] digits) {
        int len = digits.length;
        for (int i = len - 1; i >= 0; i--) {
            digits[i]++;
            digits[i] %= 10;
            if (digits[i] != 0) {
                return digits;
            }
        }
        digits = new int[len + 1];
        digits[0] = 1;
        return digits;
    } 
```
