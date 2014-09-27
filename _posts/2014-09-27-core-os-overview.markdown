---
layout: post
title:  "CoreOS Overview"
date:   2014-09-27 15:18:00
categories: docker
---
###What is CoreOS
CoreOS is an open source lightweight operating system based on the Linux kernel and designed for providing infrastructure to clustered deployments, while focusing on automation, ease of applications deployment, security, reliability and scalability. As an operating system, CoreOS provides only the minimal functionality required for deploying applications inside software containers, together with built-in mechanisms for service discovery and configuration sharing.

###More Detail
CoreOS provides no package manager, requiring all applications to run inside their containers, using Docker and its underlying Linux Containers (LXC) operating system–level virtualization technology for running multiple isolated Linux systems (containers) on a single control host (CoreOS instance). That way, resource partitioning is performed through multiple isolated userspace instances, instead of using a hypervisor and providing full-fledged virtual machines. This approach relies on the Linux kernel's cgroups functionality, which provides namespace isolation and abilities to limit, account and isolate resource usage (CPU, memory, disk I/O, etc.) of process groups.

CoreOS uses systemd as its primary init system, with tight integration between it and various CoreOS' internal parts.