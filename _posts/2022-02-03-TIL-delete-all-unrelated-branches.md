---
layout: post
author: Pau Riosa
title: "TIL: Clean up local branches"
image_path: /assets/images/IMG_20220221_153902.jpg
keywords: "clean up local branches that no longe have references to remote repository"
---

Today I learned how to clean up local branches that no longer have references to the remote (have already been merged/shipeed/etc).
Thanks to one my work mates Moshe Paul, Backend Engineer at Papa.

```


$ git fetch --prune
$ git branch -r | awk '{print $1}' | egrep -v -f /dev/fd/0 <(git branch -vv | grep origin) | awk '{print $1}' | xargs git branch -d

```

> Happy Coding!
