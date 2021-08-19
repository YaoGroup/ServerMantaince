# Using Conda Environment
=== A reference for [Yao Group Server Infrastructure Note](https://hackmd.io/dd8wi827SpCLAe8p2Ype6w) ===

:::info
An Conda environment is an isolated set of files/programs to execute Python scripts. By isolated, it means that **the environment works independenttly from any other Python interpreter**, including the system default ones. So users can install Python packages specifically for an environment, without affecting any other Python interpreter. 

It is essential for controlling the packages for running Python scripts. Without this, we'll encounter many "Why does the script work on my machine, but not yours?" problems.
:::

All files/programs of an Conda environment is under a single directory. For example, the environment we built for running TensorFlow 2.x codes are under /opt/anaconda3/envs/tf24. The most important programs under the environment directory are the Python interpreter (a program to execture python script, under /opt/anaconda3/envs/tf24/bin) and a set of python packages.

We have installed [Anaconda](https://docs.anaconda.com/) for all users, and provide two basic environments for standard:

> **tf115** (`conda acitvate tf115`)
> 
> the standard environment for TensorFlow 1.X codes.

> **tf24** (`conda acitvate tf24`)
> 
> the standard environment for TensorFlow 2.X codes.

> **tf114** (`conda acitvate tf114`)
> 
> Only for running [Razzi's PINN project](https://github.com/maziarraissi/PINNs)
> It uses tf.contrib and thus too old for Tensorflow 1.15

:::info
These environemnts are still minimal,
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

This is a more complex approach, but we still recommend it because experience is better. Choose an editor like [Visual Studio Code](https://code.visualstudio.com/) or [PyCharm (professional version require, though)](https://www.jetbrains.com/pycharm/). Run the jupyter notebook within the editor. The most important settings of this approach include:

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

Though non-admin users can not create named environements under /opt/anaconda3, they can still create custom environments under their other directories.

We give the step-by-step example:

1. Create and move into a target directory by `mkdir -p ~/Conda/my-env && cd ~/Conda/my-env`
2. Create/Copy an environment file, you may find the example useful at the bottom of [this page](https://hackmd.io/7PUOhT4GREysoZkAwp-3Ag).
3. Create an environment by `conda env create -f ./environment.yml -p .`
4. To trigger the environemt, we have to specify the path: `conda env activate ~/Conda/my-env`

Note: though environment file is recommended, but it's not the only way to create an environemnt with desired packages. Check out the [official document](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).

#### Q: I want to add some packages into existing environments

Though we recommend to create an environment file, this approach can be too restricted when experimenting with packages.

To add packges into existing environments, instead of create new ones:
1. Activate the target environment (`conda activate ~/Conda/my-env`)
2. Run `conda install my-target-package`, then the packge is added into the target environment.

Note: non-admin users can not change the standard environments under /opt/anaconda3/envs, as expected.


###### addtional info: [Admin notes on HackMD](https://hackmd.io/@MingRuey/Sy3D6VAc_)
---