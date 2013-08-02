---
created: 2010-05-11 09:50
creator: pjy
description: ''
title: 分页
---
========================
分页
========================
::

  results = searchObject()
  batch = Batch(results, batch_start=40, size=20)
  batch_html = renderBatch(context, reqeust, batch)

