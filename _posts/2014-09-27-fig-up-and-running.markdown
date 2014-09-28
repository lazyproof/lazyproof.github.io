---
layout: post
title:  "Fig Up and Running"
date:   2014-09-27 16:15:00
categories: fig docker
---
## Boot2Docker
{% highlight sh %}
boot2docker up
$(boot2docker shellinit)
{% endhighlight %}

Boot2Docker and Docker-osx both work by running a small VM on your OSX and running Docker from there.

## Fig