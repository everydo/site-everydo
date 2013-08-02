---
created: 2008-12-29 20:47:00
creator: 潘俊勇
description: ''
title: 分面分类
---
====================
分面分类法
====================

标签云，我一直觉得是web2.0的鸡肋，一大堆的关键字，鼓起勇气点了一个最大的，于是再也没有勇气继续点击了。

百度百科的开放分类，是在解决这个问题，看看他们的分类：

http://baike.baidu.com/

有序的三级分类，是不是清晰很多了？
我估计是百科的编辑群，对新增的分类进行整理归纳，形成了这个庞大的分类索引。

于是我继续寻找这种分类方法的科学依据，找到了 http://facetag.org . faceted tag, 或者说分面的分类方法，是web 2.0上比较新的分类技术，他可支持单层或者多级的分类. 先看看这个使用的flash示例：

http://facetag.org/download/facetag.swf

MIT专门开发了一个web服务，你可轻松内嵌这个功能到你的网站：

http://simile.mit.edu/exhibit/

drupal的分类系统，其实就支持这个的:

http://theploneblog.org/blog/archive/2006/05/31/death-and-taxonomies

Plone上也有个产品:

http://plone.org/products/faceted-navigation

这2个产品，都不支持网站局部的分类体系，只能定义全局的分类。这不适合进行分区管理的。而且plone的那个产品不支持多层的定义。

从前学习过多维分析／数据挖掘的，这些分类实际上是一些用户定义的维度(facet)，每个维度可能分多个级别(level)，这个是做多维的查询而已。

除了这些用户定义的维度，还支持自动生成的维度的，比如时间、状态之类，但是这方面的信息通常被用作查询条件。

