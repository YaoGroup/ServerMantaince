## Using Conda Environment Remotely with Visual Studio Code

This guide teaches how to use Visual Studio Code to develop jupyter notebook on our workstation.

### 1. Install

Install [Visual Studio Code](https://code.visualstudio.com/). It should be as easy. Download then click the installer.

### 2. Remote Devlopement
* a. Create an SSH identify following [this guide](https://stackoverflow.com/questions/31813080), this will create a pair of files, a **id_rsa** & **id_rsa.pub** file

* b. Copy the content of **id_rsa.pub** file to ~/.ssh/authorized_keys on the workstation. Create the authorized_keys file if it does not exist 
:::warning
Security: make sure **Any Other CAN NOT** read authorized_keys file!
:::

* c. Click the Extensions on the left panel, install Remote-SSH extension. The extension allows us to access the workstation within VSCode via SSH. ![](https://i.imgur.com/a1CnKAh.png)
* Press `Ctrl + Shift + P` to trigger Command Palette (or similarly, click View->Command Palette). Select `Remote-SSH: Connect to Host...` , select `Configure SSH Hosts` and open a configuration file. 
![](https://i.imgur.com/IjFvPo2.png) 
![](https://i.imgur.com/IAn8UrJ.png)

* d. Type the follings into the configuration file, but remeber to **change the User to your username on workstation**, and **IdentityFile with the id_rsa file created in step a**.
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

* b. Select the desired Python interpreter

:::success
VSCode is smart. By selecting correct interpreter path, it will load the corresponding Conda environments.

**For systemwise tf115** Environment: 
`/opt/anaconda3/envs/tf115/bin/python`

**For systemwise tf24** Environment: 
`/opt/anaconda3/envs/tf24/bin/python`
:::

* c. Open an Jupyter Notetook file, things should work.