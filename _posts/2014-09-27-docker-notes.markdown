---
layout: post
title:  "Docker Notes"
date:   2014-09-27 13:39:00
categories: docker
---
###What is docker?
Docker is an open-source project that automates the deployment of applications inside software containers, by providing an additional layer of abstraction and automation of operating system–level virtualization on Linux.

Docker uses resource isolation features of the Linux kernel such as cgroups and kernel namespaces to allow independent "containers" to run within a single Linux instance, avoiding the overhead of starting virtual machines.

Linux kernel's namespaces completely isolate an application's view of the operating environment, including process trees, network, user IDs and mounted file systems, while cgroups provide resource isolation, including the CPU, memory, block I/O and network. Docker includes the libcontainer library as a reference implementation for containers, and builds on top of libvirt, LXC (Linux containers) and systemd-nspawn, which provide interfaces to the facilities provided by the Linux kernel.

###What are docker Layers?
Union mount - Combining filesystems
Adds a read-write file-system over the read-only file system. There may be multiple read-only file-systems stacked on top of each other.

We think of each of these file systems as a layer

###What are docker Images?
A Read-only Layer is called an image.

An image never changes and therefore have no state.

###What is the init process?

###Why use phusion base images?

###File Permissions

###Getting a basic Rails implementation running