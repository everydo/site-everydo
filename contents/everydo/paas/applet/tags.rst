---
created: 2010-04-29 09:25
creator: pjy
description: ''
title: 标签组
---
=============================
标签组
=============================

ITagsManager ：标签组管理接口
-----------------------------------------

- listTags(): 得到全部Tags
    
- addTag(tag, exclude=False): 添加一个Tag, 如果exclude，则添加的时候，
  把FaceTag的同一类的其他标签删除
    
- delTag(tag): 删除指定Tag
    
- canEdit(): 是否可以编辑


IFaceTagSetting
---------------------------------
标签组设置::

    def getFaceTagText():
        """ 得到face tag 文字"""

    def setFaceTagText(text):
        """ 设置face tag文字，会自动转换的, 典型如下:

            按产品
            -wps
            -游戏
             --天下
             --传奇
            -毒霸

            按部门
            -研发
            -市场 
        """

    def getFaceTagSetting():
        """ 得到全部的face tag setting

            [(按产品, (wps, (游戏, (天下, 传奇)), 毒霸)),
             (按部门, (研发, 市场))]
        """

如何改变设置流程单的状态? 并支持搜索
--------------------------------------------------
比如故障完成与否？

我们推荐使用标签组来搜索，需要在流程右侧分组设置可用的标签。

添加一个标签::

  ITagManager(sheet).addTag('完成')

希望同时去除这个标签组中的其他的状态， 比如"处理中"这样的状态，因为二者不能同存::

  ITagManager(sheet).addTag('完成', exclude=True)

一般采用后者。
