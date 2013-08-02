---
created: 2010-04-29 09:26
creator: pjy
description: ''
title: 状态管理
---
===========================
状态管理
===========================

statemachine_xxx：保密和发布流程

对象自身的流程包括：

statemachine_modify: 发布流程
---------------------------------

  状态包括：

  - modify.default, 草稿
  - modify.pending, 待审
  - modify.archived，发布/存档 (只读)

::

   (State('modify.default', 'Draft', 'Did not submit to pending, maybe modified in'), 
    State('modify.pending', 'Pending', 'Submit to pending, now being reviewed'), 
    State('modify.archived', 'Published', 'Published, it prohibite to modify')),

statemachine_visible: 保密流程
-----------------------------------
  状态包括：

  - visible.default, 普通
  - visible.private，保密

::
    (State('visible.default', 'Public', 'Visible to normal folder reader'), 
    State('visible.private', 'Private', 'Normal folder reader can not view this file.'),
    State('visible.ctrldefault', 'Public', 'Visible to normal folder reader'), 
    State('visible.ctrlprivate', 'Private', 'Normal folder reader can not view this file.')),


可设置对象的状态，比如设置状态为保密::

  statemachine_visible.setState(sheet, 'visible.private')
