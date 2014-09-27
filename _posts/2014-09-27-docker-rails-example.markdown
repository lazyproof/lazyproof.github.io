---
layout: post
title:  "Docker Rails Example"
date:   2014-09-27 13:24:00
categories: docker rails
---
Install docker on osx w/ docker-osx:
{% highlight sh %}
curl https://raw.githubusercontent.com/noplay/docker-osx/1.1.1/docker-osx > /usr/local/bin/docker-osx
chmod +x /usr/local/bin/docker-osx
docker-osx shell
{% endhighlight %}

Install fig:
{% highlight sh %}
curl -L https://github.com/docker/fig/releases/download/0.5.2/darwin > /usr/local/bin/fig
chmod +x /usr/local/bin/fig
{% endhighlight %}