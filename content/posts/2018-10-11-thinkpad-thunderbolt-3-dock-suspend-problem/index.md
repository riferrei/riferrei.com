---
title: "ThinkPad Thunderbolt 3  Dock | Suspend Problem"
author: "Ricardo Ferreira"
tags:
  - "Dock"
  - "Lenovo"
  - "ThinkPad"
  - "Workaround"
date: 2018-10-11
nolastmod: true
draft: false
---
As mentioned in [this post](https://riferrei.com/2018/10/09/new-lenovo-thinkpad-x1-extreme); I have acquired a new laptop from Lenovo, the ThinkPad X1 Extreme. Since I will be working from home sometimes, I thought it would be a good idea to buy an dock station for it.

So I decided to buy the following dock station:

![](40AN0230US-main-v1.jpeg)[ThinkPad Thunderbolt 3 Dock](https://www.lenovo.com/us/en/accessories-and-monitors/docking/universal-cable-docks-usb/Thunderbolt-230W-dock-US/p/40AN0230US)

It is a nice dock station solution, especially because it connects everything to the laptop via Thunderbolt 3. However; since I am running Fedora in my laptop, things couldn't be that easy right?

Firstly, by default any bolt-based device is not enabled in Fedora. So I have found t[his blog](https://funnelfiasco.com/blog/2018/06/29/thinkpad-thunderbolt-dock-fedora) that helped on this matter. After that all ports were working as expected. FYI, I haven't had to turn the SELinux off in order to work.

Secondly; I have found that any time I boot the laptop with the lid closed, the O.S would turn to a suspended state after the login. It was like if after the login - I would have closed the lid off. After some digging across many Fedora forums, I found a thread where people were discussing some-old-knobs-that-used-to-work-on-previous-versions.

Anyone that uses Linux might be used to these kind of thing, but I guess I haven't used Linux as much as I should to get used to it. Anyway, in one of those threads I have found the proper solution. Here are the steps:
```
   1) sudo vi /etc/systemd/logind.conf
   2) Uncomment the property **HandleLidSwitch
**   3) Set the value of this property to "ignore"
   4) sudo systemctl restart systemd-logind
```

That is it. After that you should have everything working =)
