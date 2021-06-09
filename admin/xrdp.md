# Installation Note for xRDP

1. `sudo apt-get install xrdp`
2. `sudo apt-get install xfce4`
3. `sudo ufw allow 3389`, can [change to ssh login](http://c-nergy.be/blog/?p=14965), but are more cumbersome to user
4. Add exec startxfce4 into /etc/xrdp/startwm.sh
5. Set allow_channels=false in  /etc/xrdp/xrdp.ini to avoid strange thinclient_drives directory under $HOME, [reference](https://github.com/neutrinolabs/xrdp/issues/218)
6. Change the default terminal emulator: `sudo update-alternatives --config x-terminal-emulator`, [reference](https://itsfoss.com/change-default-terminal-ubuntu/)

## Performance issue
4. [Change crpt_level to low](https://superuser.com/questions/1539900/slow-ubuntu-remote-desktop-using-xrdp)
