---
layout: post
title:  "Docker Links"
date:   2014-09-27 15:40:00
categories: docker links
---
A link creates a source container that can provide information about itself to a recipient container.

Docker creates a secure tunnel between the containers that doesn't need to expose any ports externally on the container.

Docker exposes connectivity information for the source container to the recipient container in two ways:

- Environment variables,
- Updating the /etc/hosts file.
Docker can set a number of environment variables. You run the env command to list the specified container's environment variables.

*Network port mappings are not the only way Docker containers can connect to one another. Docker also has a linking system that allows you to link multiple containers together and send connection information from one to another. When containers are linked, information about a source container can be sent to a recipient container. This allows the recipient to see selected data describing aspects of the source container.*

{% highlight sh %}
    $ sudo docker run --rm --name web2 --link db:db training/webapp env
    DB_NAME=/web2/db
    DB_PORT=tcp://172.17.0.5:5432
    DB_PORT_5432_TCP=tcp://172.17.0.5:5432
    DB_PORT_5432_TCP_PROTO=tcp
    DB_PORT_5432_TCP_PORT=5432
    DB_PORT_5432_TCP_ADDR=172.17.0.5
{% endhighlight %}

Note: These Environment variables are only set for the first process in the container. Similarly, some daemons (such as sshd) will scrub them when spawning shells for connection.

You can see that Docker has created a series of environment variables with useful information about the source db container. Each variable is prefixed with DB_, which is populated from the alias you specified above. If the alias were db1, the variables would be prefixed with DB1_. You can use these environment variables to configure your applications to connect to the database on the db container. The connection will be secure and private; only the linked web container will be able to talk to the db container.

In addition to the environment variables, Docker adds a host entry for the source container to the /etc/hosts file. Here's an entry for the web container:

$ sudo docker run -t -i --rm --link db:db training/webapp /bin/bash
root@aed84ee21bde:/opt/webapp# cat /etc/hosts
172.17.0.7  aed84ee21bde
. . .
172.17.0.5  db
You can see two relevant host entries. The first is an entry for the web container that uses the Container ID as a host name. The second entry uses the link alias to reference the IP address of the db container. You can ping that host now via this host name.

*Note: You can link multiple recipient containers to a single source. For example, you could have multiple (differently named) web containers attached to your db container.*

###Linking Containers Together

This would bind port 5000 inside the container to port 5000 on the localhost or 127.0.0.1 interface on the host machine.

{% highlight sh %}
$ sudo docker run -d -p 127.0.0.1:5000:5000 training/webapp python app.py
{% endhighlight %}

Or, to bind port 5000 of the container to a dynamic port but only on the localhost, you could use:

{% highlight sh %}
$ sudo docker run -d -p 127.0.0.1::5000 training/webapp python app.py
{% endhighlight %}

You can also bind UDP ports by adding a trailing /udp. For example:

{% highlight sh %}$ sudo docker run -d -p 127.0.0.1:5000:5000/udp training/webapp python app.py{% endhighlight %}

###Container naming
To establish links, Docker relies on the names of your containers. Make it something easy to remember. It acts as a reference point to other containers.

Links allow containers to discover each other and securely transfer information about one container to another container. When you set up a link, you create a conduit between a source container and a recipient container. The recipient can then access select data about the source. To create a link, you use the --link flag. First, create a new container, this time one containing a database.

Name your container by using the --name flag, for example:

{% highlight sh %}$ sudo docker run -d -P --name web training/webapp python app.py{% endhighlight %}

Then:

{% highlight sh %}
$ sudo docker ps -l

CONTAINER ID  IMAGE                  COMMAND        CREATED       STATUS       PORTS                    NAMES
aed84ee21bde  training/webapp:latest python app.py  12 hours ago  Up 2 seconds 0.0.0.0:49154->5000/tcp  web
{% endhighlight %}

You can also use docker inspect to return the container's name.

{% highlight sh %}
$ sudo docker inspect -f "{{ .Name }}" aed84ee21bde
{% endhighlight %}