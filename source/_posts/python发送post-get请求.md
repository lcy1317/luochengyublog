---
title: python发送post/get请求
date: 2022-05-10 16:17:13
tags: Titanium Tech
categories: Titanium Tech
author: Lcy
---

# python发送post get请求

通常情况下直接向网址请求直接调request包就好了，但是在某些自己写的api进行测试的时候常常有什么application/json的格式要求或者要在链接里加上参数，所以写了一个tools在这里remark一下。

```python
# tools.py
from dis import dis
from email import header
from logging.config import stopListening
from wsgiref import headers
import yaml
import os
import scipy.io as io
import numpy as np
import requests

def readYaml():
    curPath = os.path.dirname(os.path.realpath(__file__))
    yamlPath = os.path.join(curPath, "config.yaml")
    with open(yamlPath, encoding='utf-8')as file:
        content = file.read()

        data = yaml.load(content, Loader=yaml.FullLoader)
        return data

def urlConcat(ip,endpoint,baseurl,api):
    return "http://"+ip+":"+str(endpoint)+baseurl+api

def queryUrl(baseUrl,data):
    url = baseUrl+"?"
    for i in data.keys():
        url = url+i+"=" + data[i] + "&"
    return url

class urlTest:
    # 初始化urlTest类
    def __init__(self,ip,endpoint,baseurl,api):
        self.ip = ip
        self.endpoint = endpoint
        self.baseurl = baseurl
        self.api = api

    # 支持传入数据直接进行测试并返回结果
    def testURL(self,data,contentType = "application/json",method = "POST"):
        headers = headers = {'Content-Type': contentType}
        testBaseURL = urlConcat(self.ip,self.endpoint,self.baseurl,self.api)
        testQueryURL = queryUrl(baseUrl=testBaseURL,data=data)
        print("正在测试"+self.api+"接口，发送数据：",data," method = ",method)
        if method == "POST":
            res = requests.post(url=testQueryURL,data=data,headers=headers)
        elif method == "GET":
            res = requests.get(url=testQueryURL,data=data,headers=headers)
        else: 
            return "Wrong Method Specialized"
        return res
```

just给自己remark一下，没啥意义哈哈哈
