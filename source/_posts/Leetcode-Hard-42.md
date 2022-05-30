---
title: Leetcode-Hard-42
date: 2022-05-30 16:23:41
tags: leetcode
categories: leetcode
author: Lcy
---

# [42. 接雨水](https://leetcode.cn/problems/trapping-rain-water/)

给定 `n` 个非负整数表示每个宽度为 `1` 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。

 

**示例 1：**

![img](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/rainwatertrap.png)

```
输入：height = [0,1,0,2,1,0,1,3,2,1,2,1]
输出：6
解释：上面是由数组 [0,1,0,2,1,0,1,3,2,1,2,1] 表示的高度图，在这种情况下，可以接 6 个单位的雨水（蓝色部分表示雨水）。 
```

**示例 2：**

```
输入：height = [4,2,0,3,2,5]
输出：9
```

 

**提示：**

- `n == height.length`
- `1 <= n <= 2 * 104`
- `0 <= height[i] <= 105`

## 分析

其实这个很直观啊，两个数组存一下一个方块左边和右边的最大值就好了。

## 实现

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        maxleft = [0]*len(height)
        maxright = [0]*len(height)
        for i in range(0,len(height)):
            if i == 0:
                maxleft[i] = 0
            else:
                maxleft[i] = max(maxleft[i-1],height[i-1])
            now = len(height) - i - 1
            if now == len(height) - 1:
                maxright[now] = 0
            else:
                maxright[now] = max(maxright[now+1],height[now+1])
        
        ans = 0
        for i in range(1,len(height) - 1):
            temp = min(maxleft[i],maxright[i])
            if temp > height[i]:
                ans += temp - height[i]
        return ans
```

