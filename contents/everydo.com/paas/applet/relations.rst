---
created: 2010-06-04 09:44
creator: 潘俊勇
description: ''
title: 关系
---
========================================
关系
========================================

关系类型
==============
1. 父子关系: children

   主要是分解，比如任务的分解，计划的分解

2. 附件: attachment

3. 关联: related

   一般关联，比如工作日志和任务之间的关联

4. 评注中的附件，和被评注对象之间的关联

   comment_attachment

5. 内容与收藏之间的关联 

   favorit

关系操作
===================
::

    for obj in relations.findTargets(self,'attachment'):
        print getName(obj)
