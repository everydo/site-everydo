---
created: 2010-04-29 09:50
creator: pjy
description: ''
title: 人员和组织架构
---
=======================
人员和组织架构
=======================

org_info
------------------------
组织结构人员信息查询的utility,name为空

- getPrincipalInfo(user_id)
  得到人员的信息，名称、手机、邮件
  返回格式为::

    {"title":full_name, "email":email,"mobile":personal_phone,'groups':[group1,group2]}
    
- listUserGroups(user_id)
  得到用户所属的组/部门
  返回格式为包含组的list

- listGroupMembers(group_id)
  得到部门/组的成员
  返回格式为包含成员的list
    
- listGroupMembersDetail(group_id):
  组成员的详细信息

- listOUOnelevelMembersDetail(group_id):
  对组织架构中，单层的组成员

- listOrgStructure():
  得到组织架构

- getUserManager( user_id, managers_table)
  查找管理人表，找到用户的所属的管理人
  managers_table，是一个如下的表格::

    [{'manager':'users.usera', 'members':['users.userb', 'groups.tree.default']}]

  界面上展现像这样:

        ====================== ====================================
        manager                members
        ====================== ====================================
        管理人A                所管理的人员、岗位、部门
        ---------------------- ------------------------------------
        管理人B                所管理的人员、岗位、部门
        ====================== ====================================
        
示例::

    >>> org_info.getUserInfo("users.wayhome")
    {"title":u'杨昆', "email":yangkun@zopen.cn,"mobile":1234567,
    'groups':['groups.tree.default','groups.tree.81729']}


