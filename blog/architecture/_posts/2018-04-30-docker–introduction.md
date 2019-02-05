---
layout: post
title: "Docker – Introduction"
date: 2018-04-30
author: ehsan
excerpt_separator: <!--more-->
---

As developers, we used to install virtual machines to use as development sandbox or install software in the different environment or OS as our local machine.
However, virtual machines consume a lot of our local resources and each installation required lots of efforts and time.

Containers, on the other hand, are much more flexible and faster, require a lot less local machine resource and are easier to distribute.
<!--more-->
#### Docker containers

Docker has made working with containers a breeze in Linux, Mac, and Windows.

Just install the Docker machine and pull (download) and run the images inside the machine.

#### Docker for Microservice

A solution based on Microservice architecture requires independent systems communicating with each other. Though you can use Azure or AWS to host those environments, that’s going to be costly for test cases. Docker enables you to create as many different environments as you wish or need easily on your local machine.

#### Docker for Deployment

One of the common issues developers have always had was the difference between their local development environment and the deployment servers – installed modules, OS version, and etc.

With Docker, you can develop inside a managed isolation and publish the same image all the way to other environments, such as Staging and production. Nowadays, all modern CI/CD tools and cloud servers support container release and deployment.
