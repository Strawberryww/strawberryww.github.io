---
layout: post
title: Install Jekyll on OEL7
tags:  [Jekyll]
categories: [first_categories]
author: wpwang
---

Jekyll is a tool for transforming your plain text into static websites and blogs. It is simple, static, and blog-aware. Jekyll uses the Liquid templating language and has builtin Markdown and Textile support.

Test Environment:
{% highlight bash %}
OS: OEL7.3
Jekyll: 3.5.1
{% endhighlight %}
Jekyll requires the version of Ruby 2.1.0 at least, but OEL7 doesn't contain it in the repository.
+ Install RVM

RVM is designed from the ground up to make the whole process of getting Ruby and managing environments easy. It is no surprise that getting RVM itself is simplified as well.
{% highlight bash %}
curl -L get.rvm.io | bash -s stable
{% endhighlight %}
If you encounter
{% highlight bash %}
GPG signature verification failed for '/usr/local/rvm/archives/rvm-1.29.2.tgz'
{% endhighlight %}
Please issue follwoing command according to the tips:
{% highlight bash %}
gpg2 --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
{% endhighlight %}
+ Install Ruby 2.1.0
{% highlight bash %}
source /etc/profile.d/rvm.sh
rvm reload
rvm install 2.1.0
gem install jekyll
{% endhighlight %}
To see all the installed Ruby versions, use the following command:
{% highlight bash %}
rvm list rubies
{% endhighlight %}
+ Run first sample
{% highlight bash %}
gem install bundler
jekyll new test
cd test
jekyll serve
{% endhighlight %}
At last, use browser to visit the 4000 port to display the sample.
