---
created: 2010-03-26 10:54
creator: 潘俊勇
description: ''
title: 易度API参考
---
===========================
易度API参考
===========================

.. Contents::
.. sectnum::

应用系统变量
==================
- package: 所在软件包
- appletsetting: applet的设置

可以用的模块
==================
这里是脚本开发中默认可以使用的Python内置模块，详细使用方法见Python标准库说明

- time
- random
- hashlib
- datetime 日期操作库
- time  时间操作库
- urllib2: 访问外部网络资源
- __builtins__ : 内置的函数及其他对象，列表如下::

    False', 'None', 'True', 'abs', 'basestring', 'bool', 'callable',
    'chr', 'cmp', 'complex', 'divmod', 'float', 'hash',
    'hex', 'id', 'int', 'isinstance', 'issubclass', 'len',
    'long', 'oct', 'ord', 'pow', 'range', 'repr', 'round',
    'str', 'tuple', 'unichr', 'unicode', 'xrange', 'zip'


函数
=================
getRoot(contet)
  根节点

getParent(context)
  得到父节点

getName(context)
  得到对象的name

absoluteURL(obj, request)
  得到某个对象的URL

checkPermission(permissoin, obj)
  检查当前用户对某个对象是否有某个权限

``searchObjects(query={}, sort_index=None, reverse=False, limit=None, restricted=True, **kw)``
    搜索函数 , kw里面可能也是查询条件，和query类似，这个是参照Plone的
    subjects=[], path='', start=(), end=(), 

getDisplayTime(time, format)
    """ 人性化的时间显示: (支持时区转换)

    time 是datetime类型，或者timestampe的服点数，
    最后的show_mode是如下:

    - localdate: 直接转换为本地时间显示，到天
    - localdatetime: 直接转换为本地时间显示，到 年月日时分
    - localtime: 直接转换为本地时间显示，到 时分
    - deadline: 期限，和当前时间的比较天数差别，这个时候返回2个值的 ('late', '12天前')
    - humandate: 人可阅读的天，今天、明天、后天、昨天、前天，或者具体年月日 ('today', '今天')

    """

全局工具
========================


intids: 对象注册表
------------------------------
intids将所有对象注册为一个整数，可通过这个整数来查询对象。

- getObject(int_id): 

  通过整数得到某个对象。


对象转换接口
==================
我们常见的电源适配器，让交流220V变成低压的直流电源，实现了一种接口到另外一种接口的转换。

这里的对象转换接口也称为适配器，同样，可以实现将对象的基本接口转换成其他的接口。

比如对象::

  >>> INewInterface(obj).method(arg1, arg2)
  >>> INewlInterface(obj).attribute

IDublinCore：标准元数据
--------------------------------------------
国际标准Dublin Core，最早用于图书馆信息索引,IDublinCore适配器用于读取dublin core数据

例如::

  >>> dc = IDublinCore(obj)
  >>> dc.title
  'the title'
  >>> dc.description
  'my desc'
  >>> dc.creators
  ['users.panjunyong']

IFieldStorage：对象数据存取接口
-----------------------------------------
IFieldStorage适配器，用于流程数据存取管理，操作方法类似Python中dict对象

使用方法如::

  >>> print IFieldStorage(flow).keys()
  ['sheet1','title','description']

  >>> print len(IFieldStorage(flow).values())
  3

  存数据:

  >>> IFieldStorage(flow)['title'] = u'你好'

  读取数据:

  >>> IFieldStorage(flow)['title']
  u'\u4f60\u597d'

  删除数据:

  >>> del IFieldStorage(flow)['description']


ITinyTable: 批量数据查询统计接口
-------------------------------------------------
对流程中的动态表格进行操作，可以列出指定行，表达式计算

- queryRows(``**kw``): 列出满足指定条件的数据行,kw指定列的条件
    
- sum(expr): expr 是一个表达式, 比如 "price * num"

"IObjectMover"：对象移动接口
-----------------------------------

"INameChooser"：名字选择接口
-----------------------------------


