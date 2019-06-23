---
title:  What type is that (unmounted) file system?
date: 2019-05-30 12:00
image: http://placehold.it/900x300
lead: "We pay a huge price for the underlying complexity of dynamic code 
running on a server for every request - a price we could avoid paying 
entirely when this kind of complexity is not needed."
subtitle: create a ultra fast, secure blog that is easy to maintain and easy to scale
---

On [2019-04-17](https://github.com/rjimeno/today_i_learned#2019-04-17) I wrote about a neat way to obtain the type of a file system __that is already mounted__. That's not the only way, but it is a neat one. The problem with it is that it requires the file system to be mounted and, the core problem is that, sometimes we do not know the type of a file system that we want to mount and it is for that reason that we cannot mount it; kind-of chicken-and-egg problem!

There is an elegant solution to that: Turns out the ```file``` command can find out the type of a file system as follows:

```bash
$ sudo file -s /dev/sda1
```

Where ```/dev/sda1``` represents the partition whose file system type is unknown. Alternatively,

```bash
$ lsblk -f
```

should also list the file system types of all the block devices.

