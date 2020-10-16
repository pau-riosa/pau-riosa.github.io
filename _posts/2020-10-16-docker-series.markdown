---
layout: post 
title:  "Docker Series: Remove unused Container"
date:   2020-10-16
author: 
description: ""
---


### Remove containers all at once
> if you have lots of stopped containers and would you like to remove, in your terminal simple put 
````
$ docker rm ${docker ps -a -a}

````
