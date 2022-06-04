---
title: k8s token generate
date: 2022-04-08 15:58:27
tags: Personal-Tips
categories: Titanium Tech
author: Lcy

---

Personal Tips. Only for my k8s.

```shell
ssh root@api.k8s-prod-hkg01.prod.bcollie.net
kubectl get secret -n kubernetes-dashboard $(kubectl get serviceaccount kubernetes-dashboard-user -n kubernetes-dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
```
Webpage：

https://k8s-dashboard.corp.bcollie.net/#/service?namespace=default
