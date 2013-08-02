---
created: 2010-06-03 09:29
creator: 潘俊勇
description: ''
title: 任务的接口
---
===========================
任务的接口
===========================
::

    class ITask(Interface):
        """ 任务 """
        
        start = zope.schema.Datetime(title=u"起始时间")
        
        end = zope.schema.Datetime(title=u"期限")

        finish_time = zope.schema.Datetime(title=u"结束时间")

        level = zope.schema.Choice(title=u"任务等级",
                vocabulary="TaskLevels")
        
        reviewer = zope.schema.Text(title=u"检查人")

        responsible = zope.schema.Text(title=u"责任人")

        progress = zope.schema.Int(title=u"进度")

        progress_notes = zope.schema.Text(title=u"进度说明")

        examine_notes= zope.schema.Text(title=u"任务检查点")

        real_score = zope.schema.Choice(title=u"评分",
                                   vocabulary="TaskScore")
        examine_result = zope.schema.Text(title=u"检查结果")
