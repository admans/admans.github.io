---
layout: mypost
title: Windows打开任务管理器提示找不到taskmgr.exe
categories: [任务管理器, Win11]
---

睡觉前习惯性地打开电脑看看，发现任务管理器打不开了，提示：Windows 找不到文件‘C:\Windows\system32\taskmgr.exe’。请确定文件名是否正确后，再试一次。

![taskmgr](taskmgr.png)

可以先用 sfc 命令对任务管理器进行检查先，看是否损坏：

```
sfc /verifyfile=C:\Windows\System32\Taskmgr.exe

sfc /scanfile=C:\Windows\System32\Taskmgr.exe
```

如果没有错误，可能是被第三方程序修改注册表导致，若要修复错误，只需要删除注册表的指定值：

1.右键单击"开始"菜单，单击"运行"（WinKey + R)

2.输入 regedit，回车

3.转到以下注册表项：

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\taskmgr.exe
```

4.右键，然后选择删除“taskmgr.exe”

现在就能够启动任务管理器了。