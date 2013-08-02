---
created: 2010-05-28 18:35
creator: 潘俊勇
description: ''
title: 订阅接口
---
=====================================
订阅接口
=====================================

接口::

    class ISubscriptionManager(Interface):
        """
        """

        subscribers = Tuple(title=u"订阅者")

        def setSubscribeMethods(methods):
            """ 设置订阅方式 """

        def getSubscribeMethods():
            """ 得到订阅方式 """

        def getSubscribedMembers():
            """Return a tuple of portal members who are subscribed here.
            """

        def setSubscribedMembers():
            """ """

        def subscribeMember(member):
            """Subscribe the member to this list.  Use the currently authenticated user if
            member is None.
            Do not raise an error if the member is already subscribed.
            Do raise an error if the member is 'Anonymous'.
            """

        def unsubscribeMember(member):
            """Unsubscribe the address from the mailing list.  Do not raise an error
            if the address is not currently subscribed.
            """

        def subscribeAuthenticatedMember():
            """Subscribe the currently authenticated member to this list.
            Do not raise an error if the member is already subscribed.
            Do raise an error if the member is 'Anonymous'.
            """

        def unsubscribeAuthenticatedMember():
            """Unsubscribe the currently authenticated member from this list.
            Do not raise an error if the member is not currently subscribed.
            Do raise an error if the member is 'Anonymous'.
            """

        def hasSubscriptionFor(member=None):
            """Boolean for whether the address or member is currently subscribed.
            """

        def hasSubscriptionForAuthenticatedMember():
            """ Boolean for whether the AuthenticatedMember is subscribed """

示例::

   ISubscriptionManager(context)

