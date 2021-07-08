

#### 1. 题目链接
[宝石与石头](https://leetcode-cn.com/problems/jewels-and-stones/)

#### 2. 题目描述
给定字符串J代表石头中宝石的类型，和字符串S代表你拥有的石头。S中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。
J中的字母不重复，J和S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。

#### 3. 解题思路
* 遍历jewels每个字符加入set中
* 遍历stones中字符判断是否包含在set中
* count统计



#### 4. 编码实现
``` java
public int numJewelsInStones(String jewels, String stones) {
    Set<Character> set = new HashSet<>();
    int count = 0;
    for (int i = 0; i < jewels.length(); i++) 
        set.add(jewels.charAt(i));
    for (int j = 0; j < stones.length(); j++) 
        if (set.contains(stones.charAt(j)))
            count++;
    return count;        
}
```
