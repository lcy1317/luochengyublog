---
title: Leetcode-Hard-675
date: 2022-05-23 13:43:55
tags: Leetcode
categories: Leetcode
author: Lcy
plugins: 
- mathjax
- katex
---

# [675. 为高尔夫比赛砍树](https://leetcode.cn/problems/cut-off-trees-for-golf-event/)

你被请来给一个要举办高尔夫比赛的树林砍树。树林由一个 `m x n` 的矩阵表示， 在这个矩阵中：

- `0` 表示障碍，无法触碰
- `1` 表示地面，可以行走
- `比 1 大的数` 表示有树的单元格，可以行走，数值表示树的高度

每一步，你都可以向上、下、左、右四个方向之一移动一个单位，如果你站的地方有一棵树，那么你可以决定是否要砍倒它。

你需要按照树的高度从低向高砍掉所有的树，每砍过一颗树，该单元格的值变为 `1`（即变为地面）。

你将从 `(0, 0)` 点开始工作，返回你砍完所有树需要走的最小步数。 如果你无法砍完所有的树，返回 `-1` 。

可以保证的是，没有两棵树的高度是相同的，并且你至少需要砍倒一棵树。

 

**示例 1：**

![img](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/trees1.jpg)

```
输入：forest = [[1,2,3],[0,0,4],[7,6,5]]
输出：6
解释：沿着上面的路径，你可以用 6 步，按从最矮到最高的顺序砍掉这些树。
```

**示例 2：**

![img](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/trees2.jpg)

```
输入：forest = [[1,2,3],[0,0,0],[7,6,5]]
输出：-1
解释：由于中间一行被障碍阻塞，无法访问最下面一行中的树。
```

**示例 3：**

```
输入：forest = [[2,3,4],[0,0,5],[8,7,6]]
输出：6
解释：可以按与示例 1 相同的路径来砍掉所有的树。
(0,0) 位置的树，可以直接砍去，不用算步数。
```

 

**提示：**

- `m == forest.length`
- `n == forest[i].length`
- `1 <= m, n <= 50`
- `0 <= forest[i][j] <= 109`

## 分析

很显然这是一个BFS的问题，第一步肯定是进行一个排序，作用是获得我们所需要的路径。得到路径之后通过广度优先搜索来不断的获取点对之间的距离。一旦搜索到点对之间无法抵达那么就返回-1。其余的情况就是一致累加点对之间的距离即可。

我们来分析一下复杂度。

首先第一次的排序+获得路径是一个$O(n^2logn^2)$的时间。

其次点对数量加点对间BFS是$O(n^2*m^2)$所以理论上是可以在$n^4$的时间内解决的。

当然如果是Go/C++我觉得直接暴力BFS就解决了。

## 实现

```python
move = (0, 1), (1, 0), (0, -1), (-1, 0)
class Solution:
    def cutOffTree(self, forest: List[List[int]]) -> int:
        road = []
        for i in range(0,len(forest)):
            for j in range(0,len(forest[0])):
                if forest[i][j] == 0 or forest[i][j] == 1:
                    continue
                road.append([forest[i][j],i,j])
        def mycmp(a,b): # 完全不需要，只是加深一下python3传自己的compare函数方法的记忆。
            return a[0] - b[0] 
        road.sort(key=functools.cmp_to_key(mycmp)) # 要用key=functools.cmp_to_key()
        
        ans = 0
        if forest[0][0] == 0:
            return -1

        def bfs(start, end):
            q = deque([(start, 0)])
            vis = [list(r) for r in forest]
            while q:
                cur, step = q.popleft()
                if cur == end:
                    return step
                x, y = cur
                step += 1
                for dx, dy in move:
                    if 0 <= (nx := x + dx) < len(forest) and 0 <= (ny := y + dy) < len(forest[0]) and vis[nx][ny]:
                        vis[nx][ny] = 0
                        q.append(((nx, ny), step))
            return -1

        if road[0][1] != 0 or road[0][2] != 0:
            ans = bfs((0,0),(road[0][1],road[0][2]))
        if ans == -1:
            return -1
        for i in range(1,len(road)):
            tmp = bfs((road[i-1][1],road[i-1][2]),(road[i][1],road[i][2])) # 点对之间找
            if tmp == -1:
                return tmp
            ans += tmp
        return ans
```

