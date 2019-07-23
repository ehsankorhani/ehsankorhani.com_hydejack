---
layout: post
title: Docker
description: >
  Docker Commands.
author: ehsan
excerpt_separator: <!--more-->
---

> A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application
>
> **docker.com**
<!--more-->

### Installation
On windows Pro, Hyper-V needs to be enabled. Then it's just the matter of downloading and running the installer.
You can also use Windows Subsystem for Linux.
Docker cannot be installed on Windows Home.

Installation on linux is more straight forward.

Just run this command: 

```bash
$ curl -sSL https://get.docker.com/ | sh
```

## Bacic commands

**Running a Container**

>docker run \<image> [command]

This is equivalanet to:

>docker create \<image>  
>docker start -a <container-id> [command]  
>[docker attach]  

**-a** in the *start* command is to watch for output/attach  

example:

```bash
$ docker run redis
```

**Display containers on machine**

All running containers at the moment:

```bash
$ docker ps
```

And to get a list of containers ever created:

```bash
$ docker ps --all
#or
$ docker ps -a
```

**Remove every container**
```bash
$ docker system prune
```

**Getting Information about Containers**

See all the output of a container:
>docker log <container-id>

*start* command can do the same thing, but it can be expensive and time consuming.

**Stopping Containers**
To give a container a 10 second time to shutdown properly use:
>docker stop <containber-id>

To stop is immediately:
>docker kill <container-id>


**Execute additional commands in container**

>docker exec -it \<container-id> \<command>

**-i** is used for *stdin* and to make the container interactive. **-t** is to make the output prettier and allocate a pseudo-TTY.

A same pattern can be used with *run*:
>docker run -it \<image> \<command>

