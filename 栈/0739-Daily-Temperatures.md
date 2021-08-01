
#### 1. 题目链接
[每日温度](https://leetcode-cn.com/problems/daily-temperatures/)

#### 2. 题目描述
请根据每日 气温 列表 temperatures ，请计算在每一天需要等几天才会有更高的温度。如果气温在这之后都不会升高，请在该位置用 0 来代替。

#### 3. 解题思路

* 维护一个存储下标的单调栈，从栈底到栈顶的下标对应的温度列表中的温度依次递减。如果一个下标在单调栈里，则表示尚未找到下一次温度更高的下标。
* 如果栈不为空，则比较栈顶元素 prevIndex 对应的温度 temperatures[prevIndex] 和当前温度 temperatures[i]，如果 temperatures[i] > temperatures[prevIndex]，则将 prevIndex 移除，并将 prevIndex 对应的等待天数赋为 i - prevIndex，重复上述操作直到栈为空或者栈顶元素对应的温度小于等于当前温度，然后将 i 进栈。

#### 4. 编码实现
``` java
public int[] dailyTemperatures(int[] temperatures) {
    int n = temperatures.length;
    int[] ans = new int[n];
    Deque<Integer> stack = new LinkedList<>();
    for (int i = 0; i < n; i++) {
        int t = temperatures[i];
        while (!stack.isEmpty() && t > temperatures[stack.peek()]) {
            int pre = stack.pop();
            ans[pre] = i - pre;
        }
        stack.push(i);
    }
    return ans;
}
```
