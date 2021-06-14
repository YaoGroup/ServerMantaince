# Installation Note for Conda Environment

1. Follow [this](https://docs.anaconda.com/anaconda/install/multi-user/), install conda to /opt/anaconda3, but do not grant permission to create environment.
2. Create /etc/commonprofile containning: `export PATH=~/anaconda3/bin:$PATH` and source it at /etc/profile & /etc/zsh/zprofile to include /opt/anaconda3/bin to PATH.
3. Also add `export CONDA_AUTO_ACTIVATE_BASE=false` to commonprofile to prevent default base activation

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