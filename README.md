# OverTheWire: Bandit Overview

## Bandit <a href="#bandit" id="bandit"></a>

The Bandit wargame is aimed at absolute beginners. It will teach the basics needed to be able to play other wargames. **If you notice something essential is missing or have ideas for new levels, please let us know!**

### Note for beginners <a href="#note-for-beginners" id="note-for-beginners"></a>

This game, like most other games, is organised in levels. You start at Level 0 and try to “beat” or “finish” it. Finishing a level results in information on how to start the next level. The pages on this website for “Level \<X>” contain information on how to start level X from the previous level. E.g. The page for [Level 1](https://overthewire.org/wargames/bandit/bandit1.html) has information on how to gain access from [Level 0](https://overthewire.org/wargames/bandit/bandit0.html) to [Level 1](https://overthewire.org/wargames/bandit/bandit1.html). All levels in this game have a page on this website, and they are all linked to from the sidemenu on the left of this page.

You will encounter many situations in which you have no idea what you are supposed to do. **Don’t panic! Don’t give up!** The purpose of this game is for you to learn the basics. Part of learning the basics, is reading a lot of new information. If you’ve never used the command line before, a good first read is this [introduction to user commands](https://man7.org/linux/man-pages/man1/intro.1.html).

There are several things you can try when you are unsure how to continue:

* First, if you know a command, but don’t know how to use it, try the **manual** ([man page](https://en.wikipedia.org/wiki/Man\_page)) by entering **man \<command>**. For example, **man ls** to learn about the “ls” command. The “man” command also has a manual, try it! When using **man**, press `q` to quit (you can also use `/` and `n` and `N` to search).
* Second, if there is no man page, the command might be a **shell built-in**. In that case use the “**help \<X>**” command. E.g. help cd
* Also, your favorite **search-engine** is your friend. Learn how to use it! I recommend [Google](https://www.google.com/).
* Lastly, if you are still stuck, you can [join us via chat](https://overthewire.org/information/chat.html)

You’re ready to start! Begin with [Level 0](https://overthewire.org/wargames/bandit/bandit0.html), linked at the left of this page. Good luck!

**Note for VMs:** You may fail to connect to overthewire.org via SSH with a “_broken pipe error_” when the network adapter for the VM is configured to use NAT mode. Adding the setting **`IPQoS throughput`** to `/etc/ssh/ssh_config` should resolve the issue. If this does not solve your issue, the only option then is to change the adapter to Bridged mode.

