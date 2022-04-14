---
title: 博弈论小游戏结果
date: 2022-04-04 14:52:17
tags: Interests

---

# 博弈论小游戏的结果

[toc]

其实这两个游戏都是经典猜均值2/3游戏的小小变型。这里就给出简单结果了，先不分析了，以及：

<center><font color=cayon size="+3"><a href="https://www.wjx.top/vj/emyupFd.aspx">第二轮链接！！！</a></font></center>

## 无激励结果

首先我先提供一下一份此前无激励的数据，[单击下载](https://lcydesktop.oss-cn-beijing.aliyuncs.com/tmp/%E6%97%A0%E6%BF%80%E5%8A%B1%E7%9A%84%E7%BB%93%E6%9E%9C.xlsx?versionId=CAEQHxiBgIDUj7eN_xciIDlkOTkyOTZkNjQ1NjRkNzFhNWY1ZmY0MTA0NjlhNDZk)

这份数据中总共只收集到了51个结果，两个游戏的winner如下

![image-20220401122516435](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220401122516435.png)

数据量较小，按间隔5提供一下数据分布：

![image-20220401122739516](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220401122739516.png)

![image-20220401122654118](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220401122654118.png)

## 本次问卷实测
首先恭喜一下@1668131450@1584129782两个同学成功的获得了红包，相同值取的是最早填报的同学。

这次问卷总共收到了818条数据，其中有两条（事实肯定远远不止）备注了不要删去了。

### 游戏1——最接近平均数

所有数字的平均数是44.76135975757379

很奇妙的事情是当问卷数量在700之前时（没记错的话）这个数字似乎一直在44.5左右波动，有位填44.444444444444······的一度坐稳了Game 1的Winner，然后后面的问卷来了之后这个数字不断被提升。

最早是1668131450在2022/3/31 11:40:16 第65个填问卷的填了45，成为了Winner。

在此我只简单处理一下数据并给出一些分布的图片以供参考，相关代码也放在文末供有兴趣的人自行运行测试。

<center>10等分，0，50，100单列</center>

![Game1ResultDividedInto10parts](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/Game1ResultDividedInto10parts.jpg)

<center>20等分，0，50，100单列</center>

![Game1ResultDividedInto20parts](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/Game1ResultDividedInto20parts.jpg)

<center>50等分，0，50，100单列</center>

![Game1ResultDividedInto50parts](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/Game1ResultDividedInto50parts.jpg)

<center>一个个分，0，50，100单列</center>

![Game1ResultDividedInto100parts](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/Game1ResultDividedInto100parts.jpg)

### 游戏2——最接近所有数从小到大排序的2/3的数 

首先结果是70

这里很奇妙的事情是当问卷数量在300左右时（没记错的话）这个数字直到结束都是70，是因为填70的太多了吧，导致最后虽然一会往前偏一点一会往后偏一点但仍然是70。哦这里我平时pandas用的少并不知道69.9999999······被处理成70怎么办所以附件的python程序有点bug要注意一下。

最早是1584129782在2022/3/31 11:04:40 第11个填问卷的填70，成为了Winner。

在此我同样只简单处理一下数据并给出一些分布的图片以供参考，相关代码也放在文末供有兴趣的人自行运行测试。


<center>10等分，0，67，100单列</center>

![Game2ResultDividedInto10parts](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/Game2ResultDividedInto10parts.jpg)


<center>20等分，0，67，100单列</center>

![Game2ResultDividedInto20parts](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/Game2ResultDividedInto20parts.jpg)

<center>50等分，0，67，100单列</center>

![Game2ResultDividedInto50parts](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/Game2ResultDividedInto50parts.jpg)

<center>一个个分，0，67，100单列</center>

![Game2ResultDividedInto100parts](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/Game2ResultDividedInto100parts.jpg)

## 附件：Code

1.库导入&文件读取

```python
from posixpath import split
from decimal import Decimal
import pandas as pd
df = pd.read_excel("dataFinal.xlsx")
pd.set_option('precision', 30)
```

2.class 定义

```python
class game:
    def __init__(self,game1,game2,qq,time,no,thinkTime) -> None:
        self.game1 = game1
        self.game2 = game2
        self.qq = qq
        self.time = str(time)
        self.no =  no
        self.thinkTime = thinkTime

ans =[game(df.iloc[i,6],df.iloc[i,7],df.iloc[i,8],df.iloc[i,1],df.iloc[i,0],int(df.iloc[i,2].strip("秒"))) for i in range(0,len(df))]
```

3.结果获取

```python
game1ans = 0
for i in range(0,len(ans)):
    game1ans += ans[i].game1/len(ans)
print("参与人数",len(ans),"Game 1 average number: ",game1ans)
maxk = 99.999
ansk = -1
for i in range(0,len(ans)):
    # Find the only winner of game1, the minist distance
    if abs(ans[i].game1 - game1ans) < maxk:
        ansk , maxk = i , abs(ans[i].game1 - game1ans)
print("Smallest distance:",abs(ans[ansk].game1-game1ans))
print("Game1 win number:",ans[ansk].game1," WinnerQQ:",ans[ansk].qq,"填报时间:",ans[ansk].time,"填报顺序:",ans[ansk].no)
# Sort
sorted_ans = sorted(ans, key=lambda x: (x.game2,x.no))
# Start from zero so minus 1 then find the first one
# TODO: There is a pricision bug here, so don't just trust the python result. so who gives me the number 69.999999999999999999999999999999999999999999999999999999999999999999999???????
ansl = int(len(ans)*2/3)-1
for i in range(0,len(sorted_ans)):
    if sorted_ans[i].game2 == sorted_ans[ansl].game2 and sorted_ans[i].no < sorted_ans[ansl].no:
        ansl = i
print("Game2 winner position:",ansl,end = " ")
print("Game2 win number:",sorted_ans[ansl].game2," WinnerQQ:",sorted_ans[ansl].qq,"填报时间:",sorted_ans[ansl].time,"填报顺序:",sorted_ans[ansl].no)
```

4.简单画下图

```python
import matplotlib.pyplot as plt
# 这两行代码解决 plt 中文显示的问题
plt.rcParams['font.sans-serif'] = ['SimHei']
plt.rcParams['axes.unicode_minus'] = False

def drawgame1(divide,figx,figy):
    cols = ["特别的0"]
    for i in range(0,50//divide):
        cols.append((str(i*divide) + "~" + str(i*divide+divide)))
    cols.append("特别的50")
    for i in range(50//divide,100//divide):
        cols.append((str(i*divide) + "~" + str(i*divide+divide)))
    cols.append("特别的100")

    dictgame1 = {}
    for i in cols:
        dictgame1[i] = 0
    for i in range(0,len(ans)):
        if (ans[i].game1 == 0):
            dictgame1["特别的0"] += 1
            continue
        if (ans[i].game1 == 50):
            dictgame1["特别的50"] += 1
            continue
        if (ans[i].game1 == 100):
            dictgame1["特别的100"] += 1
            continue
        for j in range(0,100//divide):
            s = str(j*divide) + "~" + str(j*divide+divide)
            if ans[i].game1 > j *divide and ans[i].game1 <= j*divide+divide:
                dictgame1[s] += 1
    colsans = []
    for i in cols:
        colsans.append(dictgame1[i])
    plt.figure(figsize=(figx,figy))
    plt.bar(cols,colsans)
    plt.title('Game1 统计结果 间隔'+str(divide))
    plt.savefig("Game1ResultDividedInto"+str(100//divide)+"parts.jpg")
    plt.show()
def drawgame2(divide,figx,figy):
    cols = ["特别的0"]
    for i in range(0,66//divide):
        cols.append((str(i*divide) + "~" + str(i*divide+divide)))
    cols.append("特别的67")
    for i in range(66//divide,100//divide):
        cols.append((str(i*divide) + "~" + str(i*divide+divide)))
    cols.append("特别的100")

    dictgame2 = {}
    for i in cols:
        dictgame2[i] = 0
    for i in range(0,len(ans)):
        if (ans[i].game2 == 0):
            dictgame2["特别的0"] += 1
            continue
        if (ans[i].game2 == 67):
            dictgame2["特别的67"] += 1
            continue
        if (ans[i].game2 == 100):
            dictgame2["特别的100"] += 1
            continue
        for j in range(0,100//divide):
            s = str(j*divide) + "~" + str(j*divide+divide)
            if ans[i].game2 > j *divide and ans[i].game2 <= j*divide+divide:
                dictgame2[s] += 1
    colsans = []
    for i in cols:
        colsans.append(dictgame2[i])
    plt.figure(figsize=(figx,figy))
    plt.bar(cols,colsans)
    plt.title('Game2 统计结果 间隔'+str(divide))
    plt.savefig("Game2ResultDividedInto"+str(100//divide)+"parts.jpg")
    plt.show()
# %%
drawgame1(1,50,20)
drawgame2(1,40,20)
```

