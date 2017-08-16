---
layout: post
title: Virtual Box Tips
tags:  [VirtualBox]
categories: [first_categories]
author: wpwang
---

Some tips of using Virtual Box.

Test Environment:
{% highlight bash %}
HOST: macOS 10.12.3
VirtualBox: 5.1.26
{% endhighlight %}
+ Port forwarding

`Notice: the VM is using NAT mode.`
{% highlight bash %}
Machine->Settings->Network->Advanced->Port Forwarding
{% endhighlight %}
Add Protocol, Host Port and Guest Port, HostIP and GuestIP may left blank.

For example, if we want to forward 2222 port in the Host to 22 port in the Guest, follow below configuration:
{% highlight bash %}
Name   Protocol   Host IP   Host Port   Guest IP   Guest Port
Rule1  TCP                  2222                   22
{% endhighlight %}

+ Shared Folder
{% highlight bash %}
Machine->Settings->Shared Folders
{% endhighlight %}
Add a host folder to share with guest os. Then in the Guest os, you need issue following command to get the permission:
{% highlight bash %}
$ sudo usermod -a -G vboxsf $USER
{% endhighlight %}
you should log out and in after doing this for the change to take effetc.

+ How to change UUID in virtual box
{% highlight bash %}
VBoxManage internalcommands sethduuid "/home/user/VirtualBox VMs/drupal/drupal.vhd"
{% endhighlight %}
