# Installation Note for Conda Environment

1. Follow [this](https://docs.anaconda.com/anaconda/install/multi-user/), install conda to /opt/anaconda3, but do not grant permission to create environment.
2. `conda init` is the official way to setup the PATH for users. However, it will modify users' init script (i.e. .bashrc or similar). We avoid that by manully adding result of `conda init` into the  /etc/commonprofile.
```sh
export CONDA_AUTO_ACTIVATE_BASE=false
__conda_setup="$('/opt/anaconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/opt/anaconda3/etc/profile.d/conda.sh" ]; then
	. "/opt/anaconda3/etc/profile.d/conda.sh"
    else
	export PATH="/opt/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
```
3. Source the /etc/commonprofile for all possible shells:
> /etc/profile, /etc/bash.bashrc (for login dash, login/non-login bash)
> 
> /etc/zsh/zshrc (for zsh)

:::warning
The above does not works for non-login dash shell.
:::

5. Also add `export CONDA_AUTO_ACTIVATE_BASE=false` to commonprofile to prevent default base activation

## Environments

We install global environments to /opt/anaconda3/envs using .yml file, for example:

`sudo /opt/anaconda3/bin/conda env create -f ~/Documents/code/IceSheet/env-
tf15/environement.yml -p /opt/anaconda3/envs/tf115`



### Environment File for TF115
```xml
name: tf115
channels:
    - defaults
dependencies:
    - python=3.7.10
    - tensorflow-gpu=1.15.0
    - scipy=1.6.2
```

### Environment File for TF24
```xml
name: tf24
channels:
    - defaults
dependencies:
    - python=3.8.10
    - tensorflow-gpu=2.4.1
    - scipy=1.6.2
```