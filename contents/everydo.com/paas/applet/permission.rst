---
created: 2010-04-29 09:26
creator: pjy
description: ''
title: 权限管理
---
===============================
权限管理
===============================

IGrantManager: 授权接口
==================================
::

  IGrantManager(obj).grantRole(role, someone)

角色名字：
==================================
- zopen.PrivateReader
- zopen.Manager
- zopen.Editor 

::

  <role id="zopen.Owner" title="" />
  <role id="zopen.Collaborator" title="" />
  <role id="zopen.Responsible" title="" />
  <role id="zopen.Subscriber" title="订阅人有这个角色" />
  <role id="zopen.PrivateReader" title="超级查看人" />
  <role id="zopen.PrivateReader4" title="仅仅文件授权的时候用，不随保密变化" />
  <role id="zopen.PrivateReader3" title="仅仅文件授权的时候用，不随保密变化" />
  <role id="zopen.PrivateReader2" title="仅仅文件授权的时候用，不随保密变化" />
  <role id="zopen.PrivateReader1" title="仅仅文件授权的时候用，不随保密变化" />
  <role id="zopen.Reader" title="Read 5" />
  <role id="zopen.Reader4" title="" />
  <role id="zopen.Reader3" title="" />
  <role id="zopen.Reader2" title="" />
  <role id="zopen.Reader1" title="" />
  <role id="zopen.Accessor" title="访问者" />

系统的人员
======================
- zope.anyone: 匿名用户
- zope.authenticated: 登录用户
