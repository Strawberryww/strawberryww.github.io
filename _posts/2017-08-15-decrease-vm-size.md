---
layout: post
title: Decrease VM Disk Size on Host
tags:  [VirtualBox]
categories: [first_categories]
author: wpwang
---

After using a certain time, the disk size inside VM is not identical with the one on host. Usually, the former is smaller than latter. 

Test Environment:
{% highlight bash %}
VM: OEL7.3
HOST: macOS 10.12.3
VirtualBox: 5.1.26
{% endhighlight %}
To decrease the disk size on host, use following commands inside VM:
{% highlight bash %}
sudo dd if=/dev/zero of=/EMPTY bs=1M
sudo rm -f /EMPTY
{% endhighlight %}
Issue following command after turning off the VM:
{% highlight bash %}
VBoxManage modifyhd mydisk.vdi --compact
{% endhighlight %}
Then the disk of VM is decreased.
