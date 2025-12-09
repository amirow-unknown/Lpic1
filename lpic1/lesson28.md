---
name: lpic
lesson: "28"
topic: install x11 and (desktop environment)
number: "28"
---
![[Screenshot_2025-11-25_20-48-32.jpg]]
- the Kernel(linux core) use #Display_Manager to manage your graphical window, such as #xorg(x11 is latest) or #Wayland(newer and better). but this #Display_Manager only can make simple graphical stuff and to make something like tiling window or panel or window apps or ...., need sth more stronger. it can be connect to Window managers or Desktop Managers. but which one!
- #Window_managers: these are more lightweight cause only manage simple actions such as graphical environment, window tab, termial, .... simple stuff.
- #Desktop_managers: these are massive as much as their performance! forexample, Gnome has map, calculator, .... besides it's main goal which are windows, ...... .
----
###### We ignore xorg(11) cause it's older now, but for your knowlege, x11 works by network, means you can do process by server and use graphical environment in other pc by it's xhost and .XAuthority configure.
---
# *Graphical desktops*:

- at the first step, after booting you face to a login page that is based on **x display manager control protocol** or anothers such as GDM(for gnome)  and ssdm(for kde).
- there are some Desktop managers which 3 famous of them are GNOME(flexibility), KDE(idk), XFCE(lightweight)
----
# *Remote Desktop*
- imagine you need to have a connection such as ssh but graphical, you need Remote desktop.
- you can do it by ssh ---> ***XForwarding Yes*** 
	- but only one app can be run
- using RDP for linux:
	- VNC (virtual network computer)
	- SPICE (simple protocol for independent computing environment)
	- RDP(remote desktop protocol) ---> softwares like xrdp
