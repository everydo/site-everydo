---
created: 2010-05-27 17:09
creator: 潘俊勇
description: ''
title: 评注服务
---
=========================
评注服务
=========================

接口
===========
::

    class ICommentManager(Interface):
        """ 适配器 """

        def listComments():
            """ 得到全部评注 

               [ { 'author':, 'time':, 'email':, 'body':, } ]
            """

        def listCommentsByObject():
            """ 得到全部评注的对象 """
            
        def addComment(text, attachements, request=None):
            """ 添加一个评注

            return { 'author':, 'time':, 'body':, 'comment_object':, }
             """

        def attachable():
            """ 回复的时候，是否支持附件 """

        def getComment(id):
            """ 得到某个评注 """

    class IComment(Interface):
        """ 评注 """

        author = zope.schema.TextLine(title=u"作者")
        email = zope.schema.TextLine(title=u"邮箱")

        body = zope.schema.Text(
                   title = u"消息正文",
                   description = u"请填写消息的正文",
                   required = True)

示例
================
::

  # 添加评注
  ICommentManager(context).addComment(body, author, email)

  # 显示评注
  ICommentManager(context).listComments()

