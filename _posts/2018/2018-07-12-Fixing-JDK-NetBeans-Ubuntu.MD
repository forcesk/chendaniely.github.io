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

1.  You need to make sure to install JDK before you install NetBeans.
2.  NetBeans instaled withour errors.
3.  Triying to create a new project... "The JDK is missing and is required to run some NetBeans modules"

<!-- more -->

```
$ javac -version
```
If the answer is: **javac 1.8.0_66** <br />
good, continue reading.

> Otherwise go to install JDK [Here](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) first.

The problem is caused by your JDK's path by default in your NetBeans. <br />
By default the path is: **"/usr"** in your NetBeans config file. <br />
But I don't know why when you install the JDK 8, the default path is "/usr/lib/jvm/java-8-oracle" <br />


###  Fixing the issue

* Find the file /usr/local/netbeans-8.2/etc/netbeans.conf
* or /home/YourName/netbeans-8.2/etc/netbeans.conf

> Depends of where you install the netbeans in the first place.

* The following line needs to be set:
> netbeans_jdkhome="/usr/lib/jvm/java-8-oracle"

*And there you go!, problem fixed.*

### Tested on:
Ubuntu 16.04 <br />
Netbeans 8.2 <br />
JDK 8
