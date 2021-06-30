

#### 1. 题目链接
[有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)

#### 2. 题目描述
给定一个只包括 '('，')'，'{'，'}'，'['，']'的字符串 s ，判断字符串是否有效。

有效字符串需满足：

    左括号必须用相同类型的右括号闭合。
    左括号必须以正确的顺序闭合。



#### 3. 解题思路
* 使用栈结构，遇到左括号在栈中压入对应的右括号，遇到右括号弹出栈顶元素判断是否相同

#### 4. 编码实现
``` java
public boolean isValid(String s) {
    Stack<Character> stack = new Stack<Character>();
    for (char c : s.toCharArray()) {
        if (c == '(') {
           stack.push(')');
        } else if (c == '{') {
           stack.push('}');
        } else if (c == '[') {
           stack.push(']');
        } else if (stack.isEmpty() || c != stack.pop()) {
            return false;
        }
    }
    return stack.isEmpty();
}
```
