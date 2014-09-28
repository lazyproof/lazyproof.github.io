---
layout: post
title:  "Docker Volumes"
date:   2014-09-27 16:00:00
categories: docker volumes
---
A data volume is a specially-designated directory within one or more containers that bypasses the Union File System to provide several useful features for persistent or shared data:

* Data volumes can be shared and reused between containers
* Changes to a data volume are made directly
* Changes to a data volume will not be included when you update an image
* Volumes persist until no containers use them