# Using Long-term Storage on HPC
=== A reference for [Yao Group Server Infrastructure Note](https://hackmd.io/dd8wi827SpCLAe8p2Ype6w) ===

The [data storage of Princeton Research Computing](https://researchcomputing.princeton.edu/support/knowledge-base/data-storage) has areas for large storage supported with backup system. Our group acquires few TB space on /projects/LAI. 

There are basically two different protocols to connect directly to the storage space on local machine **SMB** and **SSH**.

:::success
User must be **inside Princeton VPN** for all the followings methods. Also the **login account and password is Princeton Net ID (with some variation for SMB, see below)** not workstation account.
:::


We show how to mount local drive to the space on SSH and/or SMB:

> **For Linux**
> 
> We can mount the folder via SSH:
> 
> `mkdir ~/tigressdata`\
> `sshfs <NetID>@della.princeton.edu:/projects/LAI ~/tigressdata`
> 
> Replace ~/tigressdata with the directory you want to mount on. And the NetID is your Princeton ID, not the one on this workstation.

> **For Mac**
> ----- Using SMB (Easier, Recommended)-----
>
> Mount /projects/LAI using SMB -- check out [this](https://ag.montana.edu/it/support/smb-macs.html). Or you prefer [do it in commnad line](https://gist.github.com/natritmeyer/6621231)
> 
> Follow the tutorial, while use `smb://tigress-cifs.princeton.edu/fileset-lai
` as path, `PRINCETON\<NetID>` as username and password of your Princeton account.
>
> ----- Using SSH -----
> 
> To use SSH protocol to mount the space. Open a terminal and install the followings using brew:
>
>`brew cask install osxfuse`\
`brew install sshfs`
>
> And following the same instruction on **Linux** section should work.

> **For Windows**
> 
> Windows has to manually install mores for mounting directory via SSH. 
> [Check out this](https://github.com/billziss-gh/sshfs-win)
>
> On the other hand, SMB is much easier (it's native for Windows). We recommend using **SMB** on Windows. Open "PC", click the "computer" at top-left, then click "Map Network Drive".
>
> Select the whatever Drive (Y:, Z:, ...) you like, and type the following into the Folder field:\
> `\\tigress-cifs.princeton.edu\fileset-lai`
> ![](https://i.imgur.com/7eoskcn.png)
>
> For credentials, type the followings:\
> account: PRINCETON\\<NetID>\
> password: your password for Princeton account
> ![](https://i.imgur.com/0s6h5Iq.png)

After mounting, accessing the directory is equavalent to access the /projects/LAI on Princeton tigressdata system. So the files copied/written into it automatically share the benefit of tigressdata, like scheduled backup .etc