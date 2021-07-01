

#### 1. 题目链接
[最小栈](https://leetcode-cn.com/problems/min-stack/)

#### 2. 题目描述
设计一个支持 push ，pop ，top 操作，并能在常数时间内检索到最小元素的栈。

push(x) —— 将元素 x 推入栈中。
pop() —— 删除栈顶的元素。
top() —— 获取栈顶元素。
getMin() —— 检索栈中的最小元素。



#### 3. 解题思路
* 使用两个栈，data栈保存数据，minStack栈保存最小值；
* 入栈时先保存到data栈，判断入栈的value值是否小于minStack的栈顶值，小于则入栈，否则将栈顶元素再次入栈
* 出栈则将对两个栈执行pop操作


#### 4. 编码实现
``` java
class MinStack {
    Stack<Integer> data;
    Stack<Integer> minStack;
    /** initialize your data structure here. */
    public MinStack() {
        data = new Stack<>();
        minStack = new Stack<>();
    }
    
    public void push(int val) {
        data.push(val);
        if (minStack.isEmpty() || val < minStack.peek()) {
            minStack.push(val);
        } else {
            minStack.push(minStack.peek());
        }
    }
    
    public void pop() {
        data.pop();
        minStack.pop();
    }
    
    public int top() {
        return data.peek();
    }
    
    public int getMin() {
        return minStack.peek();
    }
}
```
