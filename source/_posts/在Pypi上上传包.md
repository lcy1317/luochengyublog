---
title: 在Pypi上上传包
date: 2022-05-19 16:42:49
tags: Tips
categories: Useful Tools
author: Lcy
---



根据setup.py生成包

```shell
python setup.py sdist bdist_wheel
```

上传

```shell
twine upload dist/*
```

安装

```shell
pip install lcyutils==0.0.1 -i https://pypi.python.org/simple
```

