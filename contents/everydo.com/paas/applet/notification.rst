---
created: 2010-04-29 09:26
creator: pjy
description: ''
title: 通知引擎
---
====================================
通知引擎
====================================

notifie_XXX: 短信/消息/邮件通知工具 包括：

- notifier_message: 站内信息
- notifier_email: 电子邮件
- notifier_sms: 短信

主要接口：

- send (title, body, to_ids,from_id=None, exclude_ids=[],bound_obj=None)
  发送消息

  :title: 标题
  :body: 正文
  :to_ids: 收件人，是一个list或者tuple
  :from_id: (可选) 发信人
  :exclude_ids: (可选) 被排除在外的id
  :bound_obj: (可选) 绑定对象
    
示例::

  notifier_message.send(title='Hello',body='welcome to china!',to_ids=['users.yangkun','users.wayhome'],)

