---
layout: post
title:  "Spotlight search bar: The Macbook Killer "
date:   2018-07-12¿9

categories: ThingsHappens

tags:
  - MacOS
  - Issues
---

## if your MacBook it's too slow and your RAM it's never enough, may this help you.

Today in ours favorite section: "Things Happens".

![SpotLight](http://www.intego.com/mac-security-blog/wp-content/uploads/2015/01/spotlight-600x300.jpeg)

The history was simple, my macbook was dead, super hot, to slow, useless.
Looking in the "Activity Monitor" I notice that a process call "mdworker" was eating a lot of my memory, a lot of the energy from my macbook
and the disk was in trouble cause by the same process.
Searching of internet I found that process it's part of the indexing of the Spotlight search bar, useless bar (for searching, I mean nobody use that search). 
Thanks Apple.

![Activity Monitor](https://www.howtogeek.com/wp-content/uploads/2015/09/ActivityMonitorMain.png)

<!-- more -->

### To fix the problem: kill the spotligh service.

![System](https://images.techhive.com/images/article/2013/10/mavericks_prefs_categories-we-dont-need-em-100065975-orig.png)

1.  Go to "System Preferences" > "SpotLight". And uncheck all the categories, uncheck everything.
2.  From the finder, select “Go” > “Utilities” > “Terminal“.
3.  In terminal for disable for good, write: sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.metadata.mds.plist
4.  You can enable the Spotlight again but, why do you do that? 

*And there you go!, problem fixed.*

### Tested on:
MacOS Hight Sierra <br />
Macbook PRO <br />
