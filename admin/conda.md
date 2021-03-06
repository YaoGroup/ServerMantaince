# Installation Note for Conda Environment

1. Follow [this](https://docs.anaconda.com/anaconda/install/multi-user/), install conda to /opt/anaconda3, but do not grant permission to create environment.
2. We give up doing `conda init` for all users in /etc/commonprofile. It's unstable to various ways to trigger conda. We simple include /opt/anaconda3/bin into $PATH in /etc/commonprofile. 
~~`conda init` is the official way to setup the PATH for users. However, it will modify users' init script (i.e. .bashrc or similar). We avoid that by manully adding result of `conda init` into the  /etc/commonprofile.~~
3. Source the /etc/commonprofile for all possible shells:
> /etc/profile, /etc/bash.bashrc (for login dash, login/non-login bash)
> 
> /etc/zsh/zshrc (for zsh)

4. Also add `export CONDA_AUTO_ACTIVATE_BASE=false` to commonprofile to prevent default base activation
5. Create /etc/conda/condarc to include /opt/anaconda3/envs tor searching environments for all users.

:::warning
The above does not works for non-login dash shell.
:::

## Environments

We install global environments to /opt/anaconda3/envs using .yml file, for example:

`sudo /opt/anaconda3/bin/conda env create -f ~/Documents/code/IceSheet/env-
tf15/environement.yml -p /opt/anaconda3/envs/tf115`



### Environment File for TF115
```xml
name: tf115
channels:
    - defaults
    - conda-forge
dependencies:
    - python=3.7.10
    - tensorflow-gpu=1.15.0
    - scipy=1.6.2
    - pydoe=0.3.8
    - ipykernel=5.3.4
    - matplotlib=3.4.2
    - seaborn=0.9.0
    - jupyter=1.0.0
```

### Environment File for TF24
```xml
name: tensorflow-2.4
channels:
    - defaults
    - conda-forge
dependencies:
    - python=3.8.10
    - defaults::tensorflow-gpu=2.4.1
    - defaults::scipy=1.6.2
    - defaults::ipykernel=5.3.4
    - defaults::matplotlib=3.4.2
    - tensorflow-probability=0.12.2
    - pydoe=0.3.8
    - jupyter=1.0.0
    - pytest=6.2.4
```


### Environment File for TF114

For running [Razzi's PINN project](https://github.com/maziarraissi/PINNs).
It uses tf.contrib and thus too old for Tensorflow 1.15

```xml
name: tf114
channels:
    - defaults
    - conda-forge
dependencies:
    - python=3.7.10
    - tensorflow-gpu=1.14.0
    - scipy=1.6.2
    - pydoe=0.3.8
    - ipykernel=5.3.4
    - matplotlib=3.4.2
    - seaborn=0.9.0
    - jupyter=1.0.0
```