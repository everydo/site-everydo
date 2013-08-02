---
created: 2010-04-29 09:26
creator: pjy
description: ''
title: 数据查询搜索
---
=====================
数据查询搜索
=====================
搜索接口
================
``searchObjects(sort_index=None, reverse=False, limit=None, restricted=True, **kw)``
    搜索函数 , kw里面可能也是查询条件，和query类似，这个是参照Plone的
    subjects=[], path='', start=(), end=(), 

例如，搜索某个数据库管理器中的数据::

  searchObjects(path=container,
                object_provides=['zopen.model.interfaces.IDataItem'],
                sort_index='created', reverse=False, limit=100, restricted=True)

系统索引
================
索引类型::

  from z3c.indexer.index import TextIndex, ValueIndex, SetIndex

索引清单::

    'creators':SetIndex, # 创建人
    'title':TextIndex,    # 标题
    'subjects':SetIndex, # 这个是关键字，或者tag
    'created':ValueIndex, # 创建时间
    'modified':ValueIndex, #修改时间
    'effective':ValueIndex,#生效时间
    'expires':ValueIndex,#失效时间
    'contributors':SetIndex,#贡献者
    'responsibles':SetIndex,#负责人
    'responsible':ValueIndex,#负责人
    'identifier':ValueIndex,#编号
    'searchable_text':TextIndex, # 可全文搜索的内容
    'stati':SetIndex,#审核状态
    'path':SetIndex,  # 路径，值是父对象的uid集合，参考http://svn.zope.org/z3ext.pathindex/trunk/src/z3ext/pathindex/index.py?rev=84920&view=auto

    'start':ValueIndex,# 开始时间
    'end':ValueIndex, # 结束时间
    'amount':ValueIndex, #总量
    'allowed_principals':SetIndex, # 可查看的人
    'disallowed_principals':SetIndex, # 禁止查看的人
    'object_provides':SetIndex, # 对象提供的接口
    'size':ValueIndex, #尺寸大小的索引
    'total_size':ValueIndex, #总大小的索引,目前用于文件:文件大小+版本大小
    'reviewer':SetIndex, #检查人
    'level':ValueIndex, # 级别


IObjectIndexer：对象索引接口
=========================================
索引对象适配器，用于修改后重建索引

- reindexObject(recursive=False): 重建全部索引,recursive是否递归
    
- reindexPath(recursive=True): 重建路径索引,recursive是否递归
    
- reindexSecurity(recursive=True): 重建权限索引,recursive是否递归

