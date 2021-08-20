# Using Conda Environment Remotely with Visual Studio Code

This guide teaches how to use Visual Studio Code to develop jupyter notebook on our workstation.

### 1. Install

Install [Visual Studio Code](https://code.visualstudio.com/). It should be easy. Download then click the installer.

### 2. Remote Devlopement
* a. Set up the key-based authentication between you local PC/laptop and the server. You can follow [this guide](https://hackmd.io/9iVBJfITQwy8tIz9ubgorw?view#Tutorial-and-tips-for-SSH-login)

* b. Click the Extensions on the left panel, install Remote-SSH extension. The extension allows us to access the workstation within VSCode via SSH. ![](https://i.imgur.com/a1CnKAh.png)

* c. Press `Ctrl + Shift + P` to trigger Command Palette (or similarly, click View->Command Palette). Select `Remote-SSH: Connect to Host...` , select `Configure SSH Hosts` and open a configuration file. 
![](https://i.imgur.com/IjFvPo2.png) 
![](https://i.imgur.com/IAn8UrJ.png)

* d. Type the follings into the configuration file, but remeber to **change the User to your username on workstation**, and **IdentityFile with the private key file (id_rsa) created in step a**.
```
Host YaoGroup
    HostName yaolab.princeton.edu
    User mc4536
    IdentityFile C:\Users\mrchou\.ssh\vscode_rsa
```

* e. Now click `Remote-SSH: Connect to Host...` again. This time an option `YaoGroup` will appear, and you be able to connet it without typing any password, and a new window will appear (password is asked, when SSH identity goes wrong, please check step a, b & d)

* f. Verify you are actually using working station by open a folder.
![](https://i.imgur.com/0r6YrPK.png)

### Develop Jupyter Notebook using Conda

* a. Install Microsoft [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) & [Jupyter extension](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)


* b. Open an Jupyter Notetook file, things should work.

* c. Select the desired Python interpreter, at the top right of notebook

![](https://i.imgur.com/6UeUM4W.png)

:::success
VSCode is smart. By selecting correct interpreter path, it will load the corresponding Conda environments.

**For standard tf115** Environment: 
`/opt/anaconda3/envs/tf115/bin/python`

**For standard tf24** Environment: 
`/opt/anaconda3/envs/tf24/bin/python`
:::

