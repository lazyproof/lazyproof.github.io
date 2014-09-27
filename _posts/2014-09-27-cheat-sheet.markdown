---
layout: post
title:  "Docker/Fig Cheat Sheet"
date:   2014-09-27 14:06:00
categories: docker fig cheat-sheet
---

##### **Pull down and look around base docker image**
{% highlight sh %}
docker run --rm -t -i phusion/baseimage:0.9.13 /sbin/my_init -- bash -l
{% endhighlight %}

###Get the fig-rails project running
{% highlight sh %}
git clone https://github.com/lazyproof/fig-rails-example.git
cd fig-rails-example
fig up
{% endhighlight %}

###Stop all docker containers
{% highlight sh %}
docker stop $(docker ps -a -q)
{% endhighlight %}

###Delete all docker images
{% highlight sh %}
docker rmi $(docker images -q)
{% endhighlight %}