---
layout: post
title: Linux kernel module hacking - Netfilter
---

Linux kernel modules are code that can be loaded and unloaded on
demand without rebooting your system. Netfilter is a powerful
framework for packet mangingling, used by iptables. It allows you to
write custom `hooks` that get executed at certain points in the packet
lifecycle.

We're going to be looking at a trivial implementation of tcpdump which
just looks at the incoming packets and counts the number of packets we
recieve from each IP-address. I'm going to go start with a trivial
kernel module and then incrementally implement our tcpdump.


{% highlight C %}

{% endlight %}


[lkmpg]: http://www.tldp.org/LDP/lkmpg/2.6/html/
[netfilter]: http://www.netfilter.org/documentation/HOWTO/netfilter-hacking-HOWTO-3.html
