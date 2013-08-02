---
created: 2010-09-03 09:39
creator: 杨小勇
description: ''
title: 新网域名服务器故障临时处理方法
---
现新网DNS服务器出现故障，导致现在 ``*.easydo.cn`` 不能正常解析

现需要手工修改本地hosts文件以支持解析

用记事本打开：

::

  c:\WINDOWS\system32\drivers\etc\hosts

添加自己站点名信息，如站点名为 **x** (**请将x替换为自己的站点名**)，
那么在最末尾处添加

::

  121.9.13.200    x.easydo.cn
  121.9.13.200    x.oc.easydo.cn

比如站点名称为: tel， 那么替换为：

::

  121.9.13.200    tel.easydo.cn
  121.9.13.200    tel.oc.easydo.cn

保存退出后， 在浏览器上输入 tel.easydo.cn即可恢复访问

