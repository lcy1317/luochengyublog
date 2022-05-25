---
title: Leetcode-Hard-699
date: 2022-05-26 00:44:55
tags: leetcode
categories: leetcode
author: Lcy
plugins: 
- mathjax
- katex
---

# [699. 掉落的方块](https://leetcode.cn/problems/falling-squares/)

在无限长的数轴（即 x 轴）上，我们根据给定的顺序放置对应的正方形方块。

第 `i` 个掉落的方块（`positions[i] = (left, side_length)`）是正方形，其中 `left 表示该方块最左边的点位置(positions[i][0])，side_length 表示该方块的边长(positions[i][1])。`

每个方块的底部边缘平行于数轴（即 x 轴），并且从一个比目前所有的落地方块更高的高度掉落而下。在上一个方块结束掉落，并保持静止后，才开始掉落新方块。

方块的底边具有非常大的粘性，并将保持固定在它们所接触的任何长度表面上（无论是数轴还是其他方块）。邻接掉落的边不会过早地粘合在一起，`因为只有底边才具有粘性。`

返回一个堆叠高度列表 `ans` 。每一个堆叠高度 `ans[i]` 表示在通过 `positions[0], positions[1], ..., positions[i]` 表示的方块掉落结束后，目前所有已经落稳的方块堆叠的最高高度。

**示例 1:**

```
输入: [[1, 2], [2, 3], [6, 1]]
输出: [2, 5, 5]
解释:

第一个方块 positions[0] = [1, 2] 掉落：
_aa
_aa
-------
方块最大高度为 2 。

第二个方块 positions[1] = [2, 3] 掉落：
__aaa
__aaa
__aaa
_aa__
_aa__
--------------
方块最大高度为5。
大的方块保持在较小的方块的顶部，不论它的重心在哪里，因为方块的底部边缘有非常大的粘性。

第三个方块 positions[1] = [6, 1] 掉落：
__aaa
__aaa
__aaa
_aa
_aa___a
-------------- 
方块最大高度为5。

因此，我们返回结果[2, 5, 5]。
```

**示例 2:**

```
输入: [[100, 100], [200, 100]]
输出: [100, 100]
解释: 相邻的方块不会过早地卡住，只有它们的底部边缘才能粘在表面上。
```

**注意:**

- `1 <= positions.length <= 1000`.
- `1 <= positions[i][0] <= 10^8`.
- `1 <= positions[i][1] <= 10^6`.

## 分析
其实要我说这个题目，我最最最最直观的想法就是线段树，因为很明显他需要处理的就是获取某一段当前的最大值，然后更新当前的最大值，就完事了。

预处理：获取一下左边界和有边界，好构造一个线段树

<span style="background-color: yellow;">但是！</span>这里也可以明显的看到`position[i][0]`的数据范围是到10^8所以肯定就是不能直接用线段树了，因为范围超了。这就很尴尬了。

再看咱就是说position.length其实是长度极为有限的。也就1000，每次顶多把一个区间加几段，不会超过3段，所以，最多就是3k个段，那么就考虑是不是可以一直维护区间。

比如对于样例一：

一开始维护[1,100000000] = 0

掉落第一个方块后维护[1,2] = 2 [3,100000000] = 0

掉落第二个方块后维护[1,1] = 2 [2,4] =5 [5,100000000]= 0

以此类推，通过各种精准的判断维护这个区间列表？

感觉逻辑上是可行的，就是写起来比较讨厌罢了。

<span style="background-color: yellow;">然而我又忘了一件事情，线段树是可以压缩的，经典的那个窗外的星星，阿不那好像是扫描线，whatever，线段树应该是可以解决的。</span>

Whatever，先实现通过

## 实现

```python
class Solution:
    def fallingSquares(self, positions: List[List[int]]) -> List[int]:
        ground = [[1,100000000,0]]
        ans = []
        for i in range(0,len(positions)):
            left = positions[i][0]
            right = left + positions[i][1] - 1 # 获得我们需要的这个方块的左右边界，然后现在就是需要得到这个方块左右边界当前的最大值。
            maxheight = 0 
            for j in range(0,len(ground)):
                l = ground[j][0]
                r = ground[j][1] 
                if (l<= left and r >=left) or (left <= l and r <= right) or (l<=right and r >=right): # 某一个区块的有边界在
                    if ground[j][2] > maxheight:
                        maxheight = ground[j][2]
                # 找到了当前的最大值。
            maxheight += positions[i][1] # 最大高度肯定是加上去了。那么下一步就是更新当前的这个ground数组。
            # print(left,right,maxheight)
            tmp = []
            for j in range(0,len(ground)):
                if ground[j][1] < left:
                    tmp.append(ground[j])
                if ground[j][0] > right:
                    tmp.append(ground[j])
                if ground[j][0] == left:
                    tmp.append([left,right,maxheight])
                if ground[j][0] < left and ground[j][1] >= left:
                    tmp.append([ground[j][0],left - 1,ground[j][2]])
                    tmp.append([left,right,maxheight])
                if ground[j][0] <= right and ground[j][1] > right:
                    tmp.append([right+1,ground[j][1],ground[j][2]])
            ground = tmp.copy()
            # print(ground)
            if len(ans) != 0:
                maxheight = max(maxheight,ans[-1])
            ans.append(maxheight) # 答案加进去
        return ans 
```

