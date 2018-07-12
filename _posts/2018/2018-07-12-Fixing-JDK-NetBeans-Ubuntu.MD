---
layout: post
title:  "How to fix NetBeans JDK issue on Ubuntu 16.04"
date:   2018-07-12

categories: ThingsHappens

tags:
  - Ubuntu
  - NetBeans
  - JDK
  - Issues
---

## Solving "The JDK is missing and is required to run some NetBeans modules"

Today in our new favorite section: "Things Happens".

* 1. You need to make sure to install JDK before you install NetBeans.
* 2. NetBeans instaled withour errors.
* 3. Triying to create a new project... "The JDK is missing and is required to run some NetBeans modules"

<!-- more -->

```
$ javac -version
```
> If the answer is: javac 1.8.0_66
> good, continue reading.
> otherwise go to install JDK first.

The problem is your netbeans don't know what your JDK is.
by default the path is: "/usr" but I don't know why, when you install the JDK 8, the default path is "/usr/lib/jvm/java-8-oracle"


## Fixing the issue

Find the file /usr/local/netbeans-8.2/etc/netbeans.conf
or /home/YourName/netbeans-8.2/etc/netbeans.conf

> Depends of where you install the netbeans in the first place.

The following line needs to be set:
> netbeans_jdkhome="/usr/lib/jvm/java-8-oracle"

And there you go!, problem fixed.

### Tested on:
Ubuntu 16.04
Netbeans 8.2
JDK 8
