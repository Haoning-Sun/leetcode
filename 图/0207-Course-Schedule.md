

#### 1. 题目链接
[课程表](https://leetcode-cn.com/problems/course-schedule/)

#### 2. 题目描述
你这个学期必须选修 numCourses 门课程，记为0到numCourses - 1 。

在选修某些课程之前需要一些先修课程。 先修课程按数组prerequisites 给出，其中prerequisites[i] = [ai, bi]，表示如果要学习课程ai 则 必须 先学习课程bi 。

#### 3. 解题思路
* 拓扑排序：使用广度优先搜索
* 使用一个队列来进行广度优先搜索。初始时，所有入度为0的节点都被放入队列中，它们就是可以作为拓扑排序最前面的节点；
* 在广度优先搜索的每一步中，我们取出队首的节点u：
    * 将u放入栈中
    * 我们移除u的所有出边，也就是将u的所有相邻节点的入度减少1。如果某个相邻节点v，的入度变为0，那么我们就将v放入队列中。
 * 在广度优先搜索的过程结束后。如果栈中包含了这n个节点，那么我们就找到了一种拓扑排序    

#### 4. 编码实现
``` java
public boolean canFinish(int numCourses, int[][] prerequisites) {
    List<List<Integer>> edges = new ArrayList<>();
    int[] indeg = new int[numCourses];
    for (int i = 0; i < numCourses; i++) {
        edges.add(new ArrayList<>());
    }
    for (int[] info : prerequisites) {
        edges.get(info[1]).add(info[0]);
        indeg[info[0]]++;
    }
    Queue<Integer> queue = new LinkedList<>();
    for (int i = 0; i < numCourses; i++) {
        if (indeg[i] == 0) {
            queue.offer(i);
        }
    }
    int visited = 0;
    while (!queue.isEmpty()) {
        visited++;
        int u = queue.poll();
        for (int v : edges.get(u)) {
            indeg[v]--;
            if (indeg[v] == 0) {
                queue.offer(v);
            }
        }
    }
    return visited == numCourses;
}
```
