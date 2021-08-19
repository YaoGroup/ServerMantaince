# Remote Access to the Server
=== A reference for [Yao Group Server Infrastructure Note](https://hackmd.io/dd8wi827SpCLAe8p2Ype6w)


The IP address of the server is *yaolab.princeton.edu*.

Before login, one must:
> 1. Contact Yao for applying an account of the server
> 2. Access internet via [Princeton VPN service](https://informationsecurity.princeton.edu/connecting-to-princeton-n) 

For commandline (CLI) usage, it provides SSH login via:

`ssh <your_account_name>@yaolab.princeton.edu`

or,

One can access desktop GUI via [Microsoft RDP](https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-clients) 


### Tutorial and tips for SSH login
---

#### Q: How can I login into the server?
It's easy. Just open any terminal like cmd. Then type and enter to execute:

`ssh <your_account_name>@yaolab.princeton.edu`

If it's your first time accessing the domain on the device, it will ask you to add the above domain into 'known hosts', type **Yes**. Then it will ask for password, type it, then you should successfully login into the server.

#### Q: How can I avoid typing password each time?

One can use terminals like [Mobaxterm](https://mobaxterm.mobatek.net/) or [Putty](https://www.putty.org/), which can remember the password locally.

One can also use [Key-Authencation](https://en.wikipedia.org/wiki/Key_authentication) based ssh login.
It involves mainly three steps:
1. Generate a key-pair on local device
2. Add public key of key-pair to the allowed identities list on target device (i.e. the server)
3. Add private key of key-pair to be the idendity of local device.

Refer [this page](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) for how to conduct those steps exactly. After the above steps, the local device is somewhat "regesitered" on the server, and ssh login no longer requires password.

---
### Tutorials on Microsoft RDP Access

#### XFCE Resources
Instead of using standard, pretty, and arguably more intuitive GNOME desktop environment, we use [XFCE](https://www.xfce.org/) since it's faster. You can find your installed applications on the top left:

![](https://i.imgur.com/sa6iVje.png)

You may want to know that dragging the application to desktop can fast create the shortcut. For other tips/questions on using the xfce, one can refer to the [official wiki page](https://wiki.xfce.org/) or do some Google.

#### Connection
Assuming we are already under Princeton VPN service.

> **For Windows**
>
> Windows has built-in **Remote Desktop Connection**, open it and connect to yaolab.princeton.edu
> 
> ![](https://i.imgur.com/MxL1Wn5.png)
>
> A login page will show up.
> Type your account and password, done!
> ![](https://i.imgur.com/3k3foQu.png)
---
> **For Mac**
>
> Download [Microsoft Remote Desktop for Mac](https://apps.apple.com/tw/app/microsoft-remote-desktop/id1295203466?mt=12), then follow the steps in Windows > section.


###### addtional info: [Admin notes on HackMD](https://hackmd.io/qW7dli1lTwi4HUW4PzEiUA)

---