

#### 1. 题目链接
[转换成小写字母](https://leetcode-cn.com/problems/to-lower-case/)

#### 2. 题目描述
给你一个字符串s，将该字符串中的大写字母转换成相同的小写字母，返回新的字符串。



#### 3. 解题思路
* 将字符串str转为字符数组
* 遍历字符数组，找到大写字母
* 将字符 += 32
* 将字符数组转回字符串类型



#### 4. 编码实现
``` java
public String toLowerCase(String s) {
    char[] array = s.toCharArray();
    for (int i = 0; i < array.length; i++) {
        if (array[i] >= 'A' && array[i] <= 'Z') {
            array[i] += 32;
        }
    }
    return new String(array);
}
```
