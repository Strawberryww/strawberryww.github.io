---
layout: post
title: Allow port on RHEL7
tags:  [Firewall]
categories: [first_categories]
author: wpwang
---

By default the port 80 for http connection is filtered on Redhat 7 as you can only access this port from the actual localhost and not from any other public host.

Test Environment:
{% highlight bash %}
OS: RHEL7.3
{% endhighlight %}
To open a port 80 on RHEL 7 Linux we need to add an iptables rule. For this RHEL7 uses firewall-cmd. First add your port 80 rule with a following command:

{% highlight bash %}
[root@rhel7 ~]# firewall-cmd --zone=public --add-port=80/tcp --permanent
{% endhighlight %}

Once you add the above firewall rule reload firewall service:

{% highlight bash %}
[root@rhel7 ~]# firewall-cmd --reload
{% endhighlight %}

And check whether the port was added to ipatables rules:

{% highlight bash %}
[root@rhel7 ~]# iptables-save | grep 80
-A IN_public_allow -p tcp -m tcp --dport 80 -m conntrack --ctstate NEW -j ACCEPT
{% endhighlight %}
