---
title: win11 恢复原右键菜单栏
date: 2021-12-16 13:20:43
tags: Tips
categories: Useful Tools
---

# Win11干掉反人类右键菜单栏

实际上只是更改一下注册表表的设置

1. win+x选择windows powershell 管理员
2. 切换成旧版右键菜单栏输入：`reg add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve`
3. 切换新版`reg delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f`
4. ctrl+shift+esc打开任务管理器重启“windows资源管理器”
