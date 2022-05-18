---
title: Leetcode-Hard-668
date: 2022-05-18 08:33:13
tags: leetcode
categories: leetcode
author: Lcy
plugins: 
- mathjax
- katex
---

# 乘法表中第k小的数

## Leetcode-668

#### [668. 乘法表中第k小的数](https://leetcode.cn/problems/kth-smallest-number-in-multiplication-table/)

几乎每一个人都用 [乘法表](https://baike.baidu.com/item/乘法表)。但是你能在乘法表中快速找到第`k`小的数字吗？

给定高度`m` 、宽度`n` 的一张 `m * n`的乘法表，以及正整数`k`，你需要返回表中第`k` 小的数字。

**例 1：**

```
输入: m = 3, n = 3, k = 5
输出: 3
解释: 
乘法表:
1	2	3
2	4	6
3	6	9

第5小的数字是 3 (1, 2, 2, 3, 3).
```

**例 2：**

```
输入: m = 2, n = 3, k = 6
输出: 6
解释: 
乘法表:
1	2	3
2	4	6

第6小的数字是 6 (1, 2, 2, 3, 4, 6).
```

**注意：**

1. `m` 和 `n` 的范围在 [1, 30000] 之间。
2. `k` 的范围在 [1, m * n] 之间。

## 分析

首先看数据范围，数据范围m，n均在1，30000之间，这意味着肯定不能强行计算之后排序获得结果。

对于$max(m,n)<=30000$的情况，先预计一下时间复杂度应该是$O(nlogn)$级别。

在这种情况下既然不能算出所有结果常见应该就这几种方法：

1. 我有一个方法能够快速跳过不可能的值
2. 我可以通过分解来完成，比如二分/递归掉原问题
3. 动态规划

Obviously第一种很难实现，但是考虑二分的时候可以想到，如果我直接去二分结果，结果也就是在$1\sim m*n$之间这样的话二分结果的复杂度是$O(log(m*n))$此后我们对于每一个结果的验证应当是简单的，我只要循环遍历m/n中间最大的那个值就可以了。中间需要处理一下细节的问题，因此复杂度应该是：
$$
O(nlog n^2)
$$
大概就是这个样子。

## 实现

Fine，从时间复杂度角度分析可以通过那就可以。直接实现去就行了，注意处理一系列的细节问题。

```python
class Solution:
    def findKthNumber(self, m: int, n: int, k: int) -> int:
        if m < n:
            m , n = n , m # make m the bigger one
        l = 1 # Define the left bound
        r = m*n # Define the right bound

        def check(num,m,n):
            tot = 0 # count the smaller numbers.
            for i in range(1,m+1):
                tmp = num // i
                if tmp > n:
                    tmp = n
                tot += tmp
            return tot
        
        while l < r: # Attention: Take care of l = r - 1 
            mid = (l + r) // 2 # Get mid 
            if check(mid,m,n) < k: # the numer smaller than mid is less than k
                l = mid
            elif check(mid,m,n) > k: # the number bigger than mid is more than k
                r = mid
            else: # yes mid is the kth one.           
                maxans = 1 # get the max num -> the answer
                for i in range(1,m+1):
                    tmp = mid // i
                    if tmp > n:
                        tmp = n
                    if maxans < tmp * i:
                        maxans = tmp * i
                return maxans
            if l == r - 1: # if don't handle this you may can't get a Accept but TimeLimitException
                return r
```

![image-20220518091027524](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220518091027524.png)
