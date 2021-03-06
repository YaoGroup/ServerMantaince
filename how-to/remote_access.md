# Remote Access to the Workstation
=== A reference for [Yao Group workstation Infrastructure Note](https://hackmd.io/dd8wi827SpCLAe8p2Ype6w) ===


The IP address of the workstation is *yaolab.princeton.edu*.

Before login, one must:
> 1. Contact Yao for applying an account of the workstation
> 2. Within Princeton network, or access internet via [Princeton VPN service](https://informationsecurity.princeton.edu/connecting-to-princeton-n) 

For commandline (CLI) usage, it provides SSH login via:

`ssh <your_account_name>@yaolab.princeton.edu`

or,

One can access desktop GUI via [Microsoft RDP](https://docs.microsoft.com/en-us/windows-workstation/remote/remote-desktop-services/clients/remote-desktop-clients) 


### Tutorial and tips for SSH login
---

#### Q: How can I login into the workstation?
It's easy. Just open any terminal like cmd. Then type and enter to execute:

`ssh <your_account_name>@yaolab.princeton.edu`

Then it will ask for password, type it, then you should successfully login into the workstation.

:::success
If it's your first time accessing the workstation on the device, it will ask you to add the workstation into 'known hosts', type `Yes`. 

You should **change your password immediately** after your first login.\
Command `passwd` can change your password.
:::

#### Q: How can I avoid typing password each time?

One can use terminals like [Mobaxterm](https://mobaxterm.mobatek.net/)(for Windows), or [iTerm2](https://iterm2.com/)(for Mac, :warning: NOT TESTED) which can remember the password locally.

One can also use [Key-Authencation](https://en.wikipedia.org/wiki/Key_authentication) based ssh login.
It involves mainly three steps:

1. Generate a key-pair on local device
    - Execute `ssh-keygen -t ed25519` in terminal
        - For the file name, one can just use the default (C:\Users\mrchou\.ssh\id_ed25519)
        - Passphrase can remain empty
        - The file id_ed25519 is the **private key**, **DO NOT** reveal it to anyone
        - The file id_ed25519.pub is **public key**, we shall add the content of this file onto workstation

2. Add public key of key-pair to the allowed identities list on target device (i.e. the workstation)
    - Login to the workstation
    - Open the file `/home/<username>/.ssh/authorized_keys`. Create the file, or even the .ssh directory if they do not exist.
        - Execute the following to create the file and the directory\
          `mkdir "~/.ssh" && touch ~/.ssh/authorized_keys`
    - Edit the file by copy the content of previous **public key file (ida_rsa.pub)** into the the authorized_keys.
        - On Windows, `type C:\Users\mrchou\.ssh\id_ed25519.pub` to display the content
            - One can also use Notepad or simlilar to open the file and view the content
            - For Mac/Linux, replace `type` with `cat`
        - Though very long, all the content of public key file is only single line.
        - One can add as many public keys into the autorized_keys file. So the file contains multiple lines, one line per public key. This make multiple machines regeistered on the the workstation.

3. After step 2, one should able to conduct the previous ssh login, without typing any password.
    - If it's not the case, it could be that your `ssh` command is not using the key.
        - Fix that by execute the followings:\
        `eval $(ssh-agent)`\
        `ssh-add /home/user-name/.ssh/ida_rsa`  (use `ssh-add` onto your private key file)



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