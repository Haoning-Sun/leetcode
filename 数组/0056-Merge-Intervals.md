

#### 1. 题目链接
[合并区间](https://leetcode-cn.com/problems/merge-intervals/)

#### 2. 题目描述
以数组 intervals 表示若干个区间的集合，其中单个区间为 intervals[i] = [start_i, end_i] 。请你合并所有重叠的区间，并返回一个不重叠的区间数组，该数组需恰好覆盖输入中的所有区间。


#### 3. 解题思路
* 首先对数组按左端数字排序
* 遍历数组，设置left和right(用于向后遍历数组)表示合并后的区间起始数组位置，leftBound和rightBound记录区间大小
* 依次对比right左端数字与rightBound，对right和rightBound进行更新
* 得到一个区间后更新left位置(即下一个区间的开始数组)

#### 4. 编码实现
``` java
public int[][] merge(int[][] intervals) {    
    Arrays.sort(intervals, new Comparator<>() {
        public int compare(int[] o1, int[] o2) {
            return o1[0] - o2[0];
        }
    });
    
    int left = 0;
    int right = 0;
    List<int[]> path = new ArrayList<>();
    while (right < intervals.length) {
        int leftBound = intervals[left][0];
        int rightBound = intervals[right][1];
        
        while (right < intervals.length && intervals[right][0] <= rightBound) {
            rightBound = Math.max(intervals[right][1], rightBound);
            right++;
        }
        path.add(new int[]{leftBound, rightBound});
        left = right;
    }
    
    int[][] res = new int[path.size()][2];
    for (int i = 0; i < path.size(); i++) {
        res[i][0] = path.get(i)[0];
        res[i][1] = path.get(i)[1];
    }
    return res;
}
```
