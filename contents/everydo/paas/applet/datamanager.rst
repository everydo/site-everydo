---
created: 2010-05-13 15:01
creator: 潘俊勇
description: ''
title: 数据管理器
---
====================================
数据管理器
====================================

基本属性
===================
:::

    def getRelatedEdoClass():
        """ 得到关联的表单定义 """

    def getRelatedWorkFlow():
        """ 得到关联的流程定义 """

表单处理
======================
::

    def renderAddForm(request, errors, template=''):
        """ return form , actions"""

    def submitAddForm(reqeust):
        """    return errors, item """

    def renderEditForm(item, request, errors, template=''):
        """    return form, ations """

    def renderDisplayForm(item, request, template=''):

    def submitEditForm(item, request):
        """    return errors, """

    def addDataItem(request, private=False, **kw):
        """ 添加数据 """

    def excuteStepAction(item, task_name, action_name, request):
        """ 执行流程步骤 """

生成模版::

   context.getRelatedEdoClass().genTemplate(omitted_fields)

添加表单处理示例::

    def renderForm(form, actions):
        return """
        <h1>易度客户调查表</h1>
        <p>您好！感谢您填写此调查表，请务必真实的告知贵公司的需求，以便我们为您提供一个适合您的方案。</p>
        <form method="post">
        %s %s
        <input type="hidden" name="form.submitted" value="1" />
        """ % (form, actions)

    template = context.getRelatedEdoClass().genTemplate(['salesman'])

    if not request.has_key('form.submitted'):
       form,actions = context.renderAddForm(request, {}, template)
       return renderForm(form, actions)
    else:
       errors, sheet = context.submitAddForm(request)
       if errors:
           form,actions = context.renderAddForm(request, errors,template )
           return renderForm(form, actions)
       else:
           return IFieldStorage(context)['finishtext']


数据处理api
=================
::

    #添加一个数据项到表格
    #data是对应的dict,如果不指定data，则创建空的dataitem
    def addRow(data = None):

    def queryRows( as_storage=False, **filter):

    def queryOneRow(**filter):
        
    def updateRows( up_data, **filter):

    def delRows( **filter):

数据访问基本api
========================
支持dict的数据访问接口::

   container.values()
   container.keys()
   container[name]
   del container[name]

IFlowTasksManager
==========================
::

    def getLastTask():
        """ 上一个完成的任务 """

    def listCurrentTasks(pid=None, state='flowtask.active'):
        """ 当前正在执行的任务对象 """

    def clear():
        """ 清除全部任务 """

    def addTask(task):
        """ 添加任务 """

    def getTask(name):
        """ 得到某个任务 """

