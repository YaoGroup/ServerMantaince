# Yao Group Server Infrastructure Note

[View it on HackMd](https://hackmd.io/dd8wi827SpCLAe8p2Ype6w)


## Remote Access to the Server

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

One can use terminals like [Mobaxterm](https://mobaxterm.mobatek.net/), which can remember the password locally.

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
> :::warning
> This section is NOT tested yet
> :::
> Download [Microsoft Remote Desktop for Mac](https://apps.apple.com/tw/app/microsoft-remote-desktop/id1295203466?mt=12), then follow the steps in Windows > section.


###### addtional info: [Admin notes on HackMD](https://hackmd.io/qW7dli1lTwi4HUW4PzEiUA)

---

## Access System-wise Conda Environment

We have installed [Anaconda](https://docs.anaconda.com/) for all users, and provide two basic environments for standard:

> **tf115** (`conda acitvate tf115`)
> 
> the standard environment for tensorflow 1.X codes.

> **tf24** (`conda acitvate tf24`)
> 
> the standard environment for tensorflow 2.X codes.

:::info
Both two environemnts are still minimal,
we plan to add more packages/settings into these via user reflection. So please let Ray/Yao knows what's missing and should be added.
:::


### Tutorials and tips for using Conda

We provide some basic tips here for fast start-up. One can also find abundant resources online, include [Princeton's Python on HPC tutorial](https://researchcomputing.princeton.edu/support/knowledge-base/python#managers).


#### Q: How can I run python script with specific environment?

0. If an account never use conda before, it first need to initialize conda via `conda init`
1. Activate desired environment via: `conda activate my_environment_name`
2. Run your script by `python my_script`

#### Q: How can I run jupyter notebook with specific environment?

It's somewhat tricker, and no single best way to achieve this. List some solutions here:

##### --- Option 1. Run Notebook with Editor

[Step by Step Guide for Visual Studio Code](https://hackmd.io/meeqtJktRfmAD-8gZwsk-g)

This is a more complex approach, but we still recommend it because experience is better. Choose an editor like [Visual Studio Code](https://code.visualstudio.com/) or [PyCharm](https://www.jetbrains.com/pycharm/). Run the jupyter notebook within the editor. The most important settings of this approach include:

* a. Make edtior into **remote development** mode, which means, the editor are able to run Python files that are located at remote, using also an interpreter on remote machine. This may require to install some extension with editor.
   > For more information:
   > 
   > VSCode, check out [this](https://code.visualstudio.com/docs/remote/remote-overview)
   > 
   > PyCharm checkout [this](https://www.jetbrains.com/help/pycharm/creating-a-remote-server-configuration.html)

* b. Make editor support exploring/executing jupyter notebook, this may require to **install some extension** with editor.
   > For more information:
   > 
   > VSCode, check out [this](https://code.visualstudio.com/docs/python/jupyter-support)
   > 
   > PyCharm checkout [this](https://www.jetbrains.com/help/pycharm/jupyter-notebook-support.html)

* c. Make sure editor uses **correct Python interpreter** to run notebooks, for example, select interpreter to `/opt/anaconda3/envs/tf24/bin/python3` will make the notebook running with tf24 conda environment.
 

##### --- Option 2. [Convert notebook to python script](https://stackoverflow.com/questions/35545402/how-to-run-an-ipynb-jupyter-notebook-from-terminal) 
and run it. For example, run`jupyter nbconvert --execute my_notebook.ipynb`

##### --- Option 3. (Not yet)
We may setup a web based jupyter notebook, so users can run notebooks directly via browser like FireFox or Chrome.

#### Q: How can I create my personal environment?

By `conda env create ...`, one can create new environment, please refer to [official documentation](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).
We suggest creating environments via yml file (`conda env create -f my_environment_file.yml`), which make environment creation reproducible, we have some sample files [here](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).


###### addtional info: [Admin notes on HackMD](https://hackmd.io/@MingRuey/Sy3D6VAc_)
---

## Mounting Long-term Storage on HPC

The [data storage of Princeton Research Computing]("https://researchcomputing.princeton.edu/support/knowledge-base/data-storage") has areas for large storage supported with backup system. Our group acquire few TB space on /projects/LAI. We show how to mount local drive to the space:

> **For Windows**
> 
> ...

> **For Linux**
>
> Case1: Mount it as **non-root** user
>
> -- Under construction --
> 
>
> Case2: Mount it as **root**
>
> -- Under construction --
> 
> It's simpler to mount smb drive as root. Check out [**this**](https://wiki.ubuntu.com/MountWindowsSharesPermanently#Mount_password_protected_network_folders). We use Ubuntu as example here. For other distributions, the process is similar. Find tools like cifs-utils for communicating with CIFS/Samba net drive.
>
> 


> **For Mac**
>
> -- Under construction --

There is also [a page on Princeton Research Computing](https://researchcomputing.princeton.edu/support/knowledge-base/tigress-cifs) on how to mount on various spaces on HPC clusters.