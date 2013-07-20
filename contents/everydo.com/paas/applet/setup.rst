---
created: 2010-04-05 19:08
creator: pjy
description: 整一个安装程序，让这些定制和脚本打包为一个产品，发给其他人使用
title: 制作安装程序
---
==========================================
制作安装程序
==========================================

到目前为止，我们这个应用的部署，全部是手工在操作。

设想，如果其他的人这么手工部署，那不是非常的用户体验差？

因此我们要整一个安装程序出来，让安装过程傻瓜化，这样这个订餐系统才能做到产品化，才能真正给其他人用了。

说到产品化，这个应用应该还:

- 需要补充一个文件库，好存放一些菜单扫描件，方便员工查看有什么菜
- 需要有个帮助页面

好了，需求就到这里，开工.


准备帮助页面
=================================
添加一个python脚本，名字为 help （帮助）::

    return """<h1>定餐系统使用帮助</h1>

    <ol>
    <li>
    必须为每个人设置初始的定餐费余额
    </li>

    <li>
    需要设置定餐单，包括定餐管理人、可选餐馆等 
    </li>

    <li>
    各个餐馆的菜单资料，可扫描后放入菜单文件夹，方便查看
    </li>

    </ol>
    """

编写安装程序
=======================
安装程序的代号必须为setup，这个和我们windows上的通常用setup.exe作为安装程序类似。

安装程序示例
-------------------
安装程序如下::

    # 部署当前组合应用
    app_container = deployApplet('zopen.dinner', context)

    # 部署订餐流程单
    dingcan_flow = deployApplet('default.datamanager', app_container, 'dingcan', '定餐单')
    dingcan_flow.setup('dincan.dingcan', workflow='dincan.dingcan')

    # 部署余额
    usermoney = deployApplet('default.datamanager', app_container, 'user_money', '餐费余额')
    usermoney.setup('dinner.user_money')

    # 部署菜单资料
    deployApplet('default.filerepos', app_container, u'files', u'菜单资料',u'定餐资料')

    # 部署添加帮助标签
    IAppletData(app_container).tabpages.append('code:help')

    request.response.redirect( absoluteURL(app_container, request))

deployApplet部署应用
--------------------------------
这里deployApplet是用来部署应用的，接口为::

   deployApplet(app_name, container, name, title)

其中：

- app_name : 是应用的名字

  对于扩展应用，这就是软件包的名字。对于基础应用，名字如下：

  - default.forum: 论坛
  - default.datamanager: 数据管理器
  - default.flowcenter: 流程中心
  - default.filerepos: 文件库
  - default.contactman:  客户中心
  - default.sites: 部门中心
  - default.projects： 项目中心
  - default.workgroup: 工作组

- container : 存放的容器

- name: 标示新对象的代号，这个代号通常是英文的，会在ur地址l中显示

- title： 部署后的栏目标题

数据管理器设置
------------------------------
对于数据库管理器，部署之后，需要设置一下关联的表单和流程::

  new_app.setup(edoclass_name, flow_name)

这里edoclass_name是表单定义的完整代号，flow_name是流程的完整代号。

调整应用的栏目
--------------------------
每个应用的标签存放在IAppletData适配器的tabpages里面，添加定制应用的一个代码::

  IAppletData(app_container).tabpages.append('code:help')

code:help是栏目的名字，栏目分为view/obj/code这几种:

- view是对基础应用才有效的，每个基础应用定义了自己的一组内建view。比如网站根有 view:desk这个view
- obj，是部署的应用，比如 obj:files ，就是前面部署的文件库，files是部署文件库的代号
- code，是定制的python脚本的名字，这里的code:help，就是help这个python脚本

部署
====================
直接使用我们的快速部署, 您一定看到最后的效果了！


