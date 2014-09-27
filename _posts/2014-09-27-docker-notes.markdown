---
layout: post
title:  "Docker Notes"
date:   2014-09-27 13:39:00
categories: docker
---
###What is docker?

###What are docker Layers?
Union mount - Combining filesystems
Adds a read-write file-system over the read-only file system. There may be multiple read-only file-systems stacked on top of each other.

We think of each of these file systems as a layer

###What are docker Images?
A Read-only Layer is called an image. An image never changes and therefore have no state.

###Why use phusion base images?

