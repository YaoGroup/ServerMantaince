# Yao Group Workstation Infrastructure Note
---

[View it on HackMD](https://hackmd.io/dd8wi827SpCLAe8p2Ype6w)

This note serves the following purpose:
- As the onboard training for anyone using the workstation for their work. It provides best practices for writing code and using the workstation to run code.
- As the reference note for fundamental technical issues or additional tips for enhancing the personal workflow.
- As the reference note for the future administrator to understand the system setup.

The note is the main page and contains links to additional references. The main page aims at onboard new comber, so they can grasp the essential concepts and start using the workstation ASAP. Other references teach one how to achieve specific things in a step-by-step way.

:::info
Before you started, check you already get an account and a password for the workstation.
And if you are outside Princeton, make sure you are using VPN.

$\small\text{^Blue boxes like this one include essential information. Make sure you read and understand.}$
:::

:::success
Feel free to ask questions. Your feedback can help us to improve this tutorial.

$\small\text{^Green boxes like this one provide useful tips and ideas on each topic.}$
:::

## Login To the Server

Open a terminal. On Windows, one can use [PowerShell](https://www.howtogeek.com/662611/9-ways-to-open-powershell-in-windows-10/). On Mac, one can open the [native terminal](https://www.howtogeek.com/682770/how-to-open-the-terminal-on-a-mac/)

Type the following into terminal, then press *enter*:
`ssh <your_account_name>@yaolab.princeton.edu`

Then it will ask for the password, type the one you get from Yao, and then successfully log into the workstation.

## A. The Basics

We start by introducing the basic concept and workflow for using the workstation. After reading through A-1 to A-3, one should be able to start working on the workstation. We hope the tutorial is concise, so everyone quickly enjoys their research work while following the best practice.

### A-1 Embrace the Command Line

Use text to control a computer is still the most robust and effective way to use a computer. We want to ensure everyone can use the workstation with text-based commands in the command line.


#### a-1.1 Know Your Home

After login, you shall see:
![](https://i.imgur.com/3BcqlE3.png)

:::info
After the welcome message, there are two important elements on the screen.

* **User Name**: The `mc4536` indicates my user name. For you, it will be your account name.
* **Location**: The text between the colon `:` and number sign `#`, in this case, it's the tilde `~`, indicated **where you are** on the computer.

$\small\text{^On a different machine, the colon or the number sign can become something else}$
:::

All files and directory in Linux forms a [Tree](https://en.wikipedia.org/wiki/Tree_(data_structure)). The slash `/` separates the names of directories and files. The root of the directory system has no name, so the root path is simply a single slash: `/`. There are many directories under root; we now only focus on a directory called **home**. The path to that directory is thus `/home`. Under home, there are multiple directories, one for each user. We'll see that in short.

:::info
There is no apparent difference between a file and a directory. For example, given a path, `/home/mc4536/Conda`, one can not tell if it is a file or directory. The fundamental difference between the two is that a directory can contain files but not vice versa.
:::

![](https://i.imgur.com/aNrTKnV.png)\
[Photo credit: TecMint](https://www.tecmint.com/linux-directory-structure-and-important-files-paths-explained/)

When you are on the workstation, at any time, you must be inside one of the directories, which is called **current working directory**. By default, after login, you are at a directory tilde `~`. Tilde `~` is a shortened form for the directory `/home/<your user name>`; this is different for every user. For example, for me, `~` means `/home/mc4536` actually.

`pwd` displays where you are. It displays the full path instead of using abbreviated tilde `~`:\
![](https://i.imgur.com/AmFe1Ou.png)

We call the tilde `~` directory, or `/home/<your user name>` simply **home**, **home directory** or **user's home**. Everyone has their home directory. We seldom need to use `/home`; thus no need for another name.

:::info
99% of the time when you are on the workstation, **you should work under your home.** You should put all your files under your home (the system prevents you from creating files at other places, anyway).
:::

#### a-1.2 Execute Command

Type `passwd` to the screen, then press *enter*. It will be the first command you type.
It's a command to change your password. Follow the instructions and set the one you like.

Now, we will give it a second shot. But this time, only type `passw` and execute. You'll get the following. You can see that the system is smart. When you type a non-existing command, it will try finding some suggestions. When you forgot a command, you may find the suggestions helpful:\
![](https://i.imgur.com/o9TROVr.png)

Now we do it the third time. This time, we type `pas`, then **click the Tab twice**, you shall see:
![](https://i.imgur.com/gmCarwM.png)

The **Tab** key is a killer feature for the command line. If you type something with a correct prefix, it will try to complete the rest. If multiple results matches, click Tab twice will display them all. It saves time for typing and the burden of remembering things.

We do it the fourth time. This time we type `info passwd`. You shall see a detailed description of the `passwd` command. Most Linux commands have a thorough document. Click `q` to exit the description.

Now we do it the last time. This time we type `passwd --help`. You shall see a summary of usage and various options of the `passwd` command.

:::info
The general form of executing a Linux command is:
![](https://i.imgur.com/RlMl1aR.png)\
\
Starting with a command, use space to separate the options, arguments for options, and arguments. `<Some Argument>` is the syntax we use for arguments in this document. `<Some Argument>` usually contains **no space**, since it uses space to separate it from other arguments.\
\
For example : 
* `passwd`
    * `passwd` is the command. We do not provide any option/argument
* `passwd --help`
    * `passed` is the command. `--help` is an option for it. We provide no argument for both the option and the command.
* `info passwd`
    * `info` is the command, and `passwd` is the argument for it.
    * To be clear, the actual running command is `info`. Although the output teaches you to use `passwd`, it does not trigger the command `passwd`.
:::

:::success
Rule of thumb: **No need to remember commands.**

You'll remember them automatically after doing it hundreds of times. Before your body is hardwired to a command, you can easily find some suggestion from the system, use Tab, read the document from `info command` and `command --help`, or simply google.
:::

#### a-1.3 Basic Command

We introduce the eight essential commands:

:::info
**Switch your working directory:**

**`cd <target directory>`**

You see that the location after your name changes.\
You can also confirm that by using `pwd`
\
\
Tips:
- `cd ..` moves "one layer up", i.e., into the parent directory.
- `cd ../..` moves "two layers up" and so on.
\
\
`..` is a convenient word for sepcifying path, like the previous tilde symbol `~`. The meaning of `..` is roughly *'the parent'*. It's not for `cd` only, you can use it with all the commands listed below. For example, `ls ..` lists the content of the parent directory.
:::

:::info
**List files/directories under a directory:**\
**`ls <target directory>`**
<br></br>
Also, the file names starting with period `.` are considered hidden. `ls` will not display them by default. One can display hidden files by adding `-a' before `<target directory>`\
![](https://i.imgur.com/ySVoiev.png)

There are quite a few hidden files under users' homes.
:::

:::info
**Copy File(s) and Directory(s)**\
`cp <file1> <file2> <file3> ... <destination>`
<br></br>
Copy all contents under directory(s):\
`cp -r <directory or file 1> <directory or file 2> ... <destination>`
:::

:::info
**Move/Rename File(s) and Directory(s)**\
`mv <source1> <source2> <source3> ... <destination>`
<br></br>
Rename is the special case of a general moving actually.\
`mv <old directory or file name> <new directory or file name>`
:::

:::info
**Create New Directory**\
`mkdir <new directory>`\
or\
`mkdir -p ./a/series/of/directory/`
:::

:::info
**Edit a Text File**\
`vim <target for edit>`

If the target does not exist, it creates a new file.
\
\
It is worth writing another book for using `vim`. For now, we only show how to start editing and quit the program.
\
\
**Start Editing**

Click `i` and check there is a text `-- INSERT --` at the bottom left. If so, you are in *insert mode* and ready to add/remove some texts. You can type/delete texts as you normally did. It's a basic mode without convenient features you used to have, for example, "undo" & "copy-paste".
\
\
**Save and Quit**

Click `esc` when you finish. It will leave insert mode. To save and quit, type a colon `:`, so that there is a `:` at the bottom left. Then type `wq` and press `enter`. It saves the content and sends you back to the command line.
:::

:::info
**Upload/Download File from Workstation**
<br></br>
**You have to execute `scp` command on your local PC, NOT the workstation**
<br></br>
Upload from the local PC to the workstation:\
`scp -r D:\what\I\want\to\upload <my-account>@yaolab.princeton.edu:/place/to/upload/`
<br></br>
Download from the workstation to the local PC -- just reverse the arguments of upload:\
`scp -r <my-account>@yaolab.princeton.edu:/target/to/download/ D:\where\I\want\to\store`
:::

:::info
**Remove Files/Directories**

Be careful, there is **no way to recover** removed files.
<br></br>
Removes File(s):\
`rm <file1> <file2> ...` 
<br></br>
Remove Empty Directory(ies):\
`rm -d <empty directory1> <empty directory2> ...`\
It removes empty directory only. If the directory is not empty, the action is blocked.
<br></br>
Remove File(s)/Directory(ies) and Its(Their) Content Recursively:\
`rm -r <directory or file1> <directory or file2> ...`\
Be careful. This will removes all things under the a directory.
:::

By combining the above commands, you can conduct all essentials on the workstation.
Though we recommend using command line, you may occasionally require a graphical user interface. We also provide that for the workstation. Please check the "Remote Access to the workstation" in References.

### A-2 Access the Code of Our Group

#### a-2-1 Access the Shared Code from GitHub

We use [GitHub](https://github.com/) as the platform for collaboratively working on projects. We'll teach you a simple way to use it for sharing the works with others.

:::info
Register an account for GitHub.

Contact Yao to allow you to access the code.
:::

#### 

GitHub has prohibited simple passwords since Aug 2021. We need to set up the authentication. It seems cumbersome but saves you from typing a password every time. Make sure you follow the instructions:  

:::info
**Setup the Authentication of GitHub**

- [Follow <u>"Generating a new SSH key"</u>](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key) section to create and add keys. 
- [Follow <u>"Adding your ssh key to the ssh-agent"</u>]( https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent) section
- Copy the content of **~/.ssh/id_ed25519.pub** and add it as a key to your GitHub account.
    - Execute `cat ~/.ssh/id_ed25519.pub` to display the content of the file in terminal
    - Click **New SSH Key** at [<u>SSH and GPG keys</u>](https://github.com/settings/keys), and copy the content into the **Key** field. 
    - Type anything you like into the **Title** field, for example, "Yao Group Workstation".
:::

Now we are ready to use GitHub. The tool we are using for code management is **Git**. GitHub tightly integrates with Git. We'll use the [Toy Example](https://github.com/YaoGroup/ToyExample) code as an example.

Switch your current working directory to a place you like, and start by execute:

`git clone git@github.com:YaoGroup/ToyExample.git`

Git will download the code from GitHub to a (new) directory *ToyExample* under the current working directory.

#### a-2-2 Upload Your Changes

`cd` into the *ToyExample* directory.

Try using `vim` or other methods to modify the README.md by adding a line below the message section. For example, Ray add his message
`Ray: Welcome! Hope the tutorials are clear and helpful!`

![](https://i.imgur.com/FYqQZ4v.png)

Save the changes, and check your changes by

`git status`

It will indicate the README.md has changed. Now we need to use Git to create a formal savepoint of the change.

:::info
The fundamental element of a version control system is a save point. Savepoint means a snapshot of what files are like at the time of saving. In Git, we call a savepoint **commit**. Also, when we use commit as a verb, it means storing changes into a commit.
:::

The first time you commit on the workstation, you have to tell Git who you are before committing.
Register your email and name by the followings:
- `git config --global user.email <your Github email>`
    - **should be exactly same as the email of your Github account**
- `git config --global user.name <your Name>`, use a name we all recognize


We are ready to commit your change by:
- Select the change to commit by `git add README.md`
- `git commit`, which will pop up vim to create a summary of your change. Here we use `Create first change for <your name>`. Save the summary as saving a file.
![](https://i.imgur.com/XdfgQw4.png)
- Upload your change by `git push`

Now, by refreshing [the project page](https://github.com/YaoGroup/ToyExample), you shall see your new message on the front page. 

#### a-2-3 Download Changes from Others
You may not be the only one working on the project. You can download the changes by execute `git pull` under the project directory when someone uploaded his changes.

:::success

- `git status` checks the file changes
- `git add <changed file1> <changed file2> ...` selects the file(s) to commit
- `git commit` commit the changes. Be sure to type a concise and meaningful summary of your changes.
- `git push` uploads the committed changes
\
\
You may want to check out the References for a more detailed explanation.  
:::


### A-3 Edit and Run The Code

We now demonstrate how to modify and run the code for Ice Sheet/Shelf projects. We use [Shelf1D](https://github.com/YaoGroup/IceShelf1D) as an example. Clone the project:

`git clone git@github.com:YaoGroup/IceShelf1D.git`


#### a-3-1 The Conda Environment

We use [Conda](https://docs.conda.io/en/latest/) to manage the environment for Python. You can learn more about the Conda environment in References. 

:::info
A Conda environment is an isolated set of files/programs to execute Python scripts. By isolated, it means that **the environment works independently from any other Python interpreter**, including the system default ones. So users can install Python packages specifically for an environment without affecting any other Python interpreter. 

It is essential for controlling the packages for running Python scripts. We'll encounter many "Why does the script work on my machine, but not yours?" problems without this.
:::

All files/programs of a Conda environment are under a single directory. For example, the environment we built for running TensorFlow 2.x codes are under `/opt/anaconda3/envs/tf24`.

#### a-3-2 Use Standard Environment to Run a Script

Run a script using a specific environment is simple. For the IceShelf1D, we use tf24 environment to run the file `script/1sr_order_forward. py' of the project:
- (First time only) setup Conda for use by `conda init`
- Activate tf24 environment by `conda activate tf24`
    - After which you shall see a `(tf24)` text before your name in terminal
- Run the script `python3 script/1st_order_forward.py`

That's all.

You can deactivate an environment by `conda deactivate`

:::success
We provide following standard environments:
<br></br>
> **tf24** (`conda acitvate tf24`)
> 
> 
> **We use this for most ice sheet/shelf projects.**\
> The standard environment for TensorFlow 2.X codes.

> **tf115** (`conda acitvate tf115`)
> 
> the standard environment for TensorFlow 1.X codes.

> **tf114** (`conda acitvate tf114`)
> 
> Only for running [Razzi's PINN project](https://github.com/maziarraissi/PINNs)
> It uses tf.contrib and thus too old for Tensorflow 1.15

addtional info: [Admin notes on HackMD](https://hackmd.io/7PUOhT4GREysoZkAwp-3Ag?view)
:::

#### a-3-3 Create Your Own Environment

Though non-admin users can not create named environments under /opt/anaconda3, they can still create custom environments under their other directories.

We give the step-by-step example:

1. Create and move into a target directory by `mkdir -p ~/Conda/my-env && cd ~/Conda/my-env`
2. Create/Copy an environment file, you may find the example useful at the bottom of [this page](https://hackmd.io/7PUOhT4GREysoZkAwp-3Ag).
3. Create an environment by `conda env create -f ./environment.yml -p .`
4. To trigger the environment, we have to specify the path: `conda env activate ~/Conda/my-env`

After activation, you can run a script by `python3 <your script>`, as we have in a-3-2.

^$\small\text{Though we recommend using an environment file, it's not the only way to create an environment. Check out}$
$\small\href{https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html}{the\ official\ documnet}$

^$\small\href{https://princeton.zoom.us/rec/share/xW-kiZmsCqcXNZkyDJudxZk59pkP3mhr-8X8jI1H3Z7Hd6_R38LLkBVXRXYrOaQD.w55FzYVTfGEWgwph}{Our\ training\ session\  recording\ might\ help}$

#### a-3-4 Edit Code and Run Jupyter NoteBook Using Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/), or VSCode, is our recommendation for editing Python code. Its ability to directly work on a remote machine, for example, our workstation, is impressive.

:::info
We provide a [<u>step-by-step</u>](https://hackmd.io/meeqtJktRfmAD-8gZwsk-g?view) walkthrough. 
:::

After you make the VSCode connects to the workstation, editing files inside VScode happens on the workstation. No upload/download or synchronization is required.

It is handy for working with Jupyter Notebook. We can remotely develop the code on the workstation and easily view the result on the VSCode. Also, we could ask VSCode to use the specified Conda environment (as we did for script in a-3-2 & a-3-3) for running the notebook:

:::info
* Install Microsoft [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) & [Jupyter extension](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)
* Open a Jupyter Notebook file. Things should work.
* Select the desired Python interpreter at the top right of the notebook

![](https://i.imgur.com/6UeUM4W.png)
<br></br>
VSCode is smart. By selecting the correct interpreter path, it will load the corresponding Conda environments. For example, **using the standard tf24** environment, we could choose:
`/opt/anaconda3/envs/tf24/bin/python`
:::




$\small\text{^There are other editors that provide similar functions. For example, PyCharm on Mac has similar features}$

## B. Usefull Skills

We provide two important skills for working on the workstation and on Princeton cluster. 

### B-1 Secure Your Long-Running Jobs (tmux)

:::success
TLDR;

Execute `tmux new -s <name>` to create a persistent terminal. Run your job inside the terminal. The workstation holds the jobs inside the terminal regardless of the internet connection. Use `tmux attach -t <name>` to get back to the terminal.
:::

To this point, we know how to use ssh to login and work on the workstation. But there is a caveat:
Launch a job, for example, `python my-job.py` within a ssh login. **If the login is disconnected, the job terminates**.

This makes long-running jobs unfeasible, especially over an unstable internet connection.

The canonical way of doing this is using a [terminal multiplexer](https://en.wikipedia.org/wiki/Terminal_multiplexer). We won't explain the mechanism behind this. We only show how to use [tmux](https://en.wikipedia.org/wiki/Tmux) to avoid the disconnection problem.

We give a simple mental model for using tmux: **When you execute `tmux` in the terminal, it creates a persistent terminal, denoted as PT, which does not end even if the internet connection is lost.**

In this section, we are going to use a simple python script `job.py` to mimic a long-running job:
```
# content of job.py
import time
from datetime import datetime

while True:
    time.sleep(1)
    print("Curent time", datetime.now())
```

Now execute `tmux new -s MyPT`. after which you are in a new terminal. Run `python job.py`, it displays the current time roughly every second. 
![](https://hackmd.io/_uploads/SknOhyHNK.png)\

Now, close the cmd, Powershell, Mobaxterm, or whatever you use to login. You can also try turning off your internet :->

Login back to the workstation again, now type `tmux ls`, it should display something like this:
![](https://hackmd.io/_uploads/BkB5jkSNt.png)\
Your terminal is still alive!

Use `tmux attach -t <MyPT>`, you shall go back to the previous terminal and see your `job.py` is still running, as if nothing happens!

:::info
`tmux`\
Start a new PT with auto-generated name. `tmux new -s <name>` does the same with given name. One can not create another PT inside a PT.
<br></br>
`tmux ls`\
Display the names of all PTs.
<br></br>
`tmux attach -t <name>`\
Get back to the PT with that name. This is the magic to use when one wants to get back the terminal previously working in after losing the connection.
<br></br>
Inside PT:\
`exit`

Outside PT:\
`tmux kill-session -t <name>`

End a PT by either (you will lose your job inside the PT).
One only needs to end PTs occasionally. It's usually for cleaning up the zombie PTs on the workstation.
<br></br>
Some other helpful tips we do not cover. For example, one can split a PT into two or more panels, which allow multiple jobs to run inside a single PT. Check out this [youtube video](https://www.youtube.com/watch?v=Yl7NFenTgIo).
:::

### B-2 Using Princeton cluster

[Princeton Research Computing](https://researchcomputing.princeton.edu/) offers bountiful computing resources. Working on the cluster is mostly the same as working on the workstation. First, Use ssh to connect to the Princeton cluster, just like our workstation. Use Della with GPU for example:

`ssh <Your Princeton ID>@della-gpu.princeton.edu`

    
However, there are crucial differences between using the cluster and the workstation:

:::info
1. One can not freely acquire computing resources (CPU & GPU). **One needs to submit their jobs via the Slurm system. All users submit their jobs to Slurm, and Slurm will determine which jobs first get executed.**
    
2. There are **no** existing Conda environments like what we provide on the workstation. You have to create on your own before using Slurm.
 
3. Using Slurm is just one step more than `python myscript.py`. **Slurm asks a text file called *Slurm script* for submitting jobs.** So the process becomes:
    - Write your `myscript.py`
    - Create Conda environment on the cluster
    - Write the Slurm script `my_submit.slurm`
        - inside the `my_submit.slurm`, specify you want to do -- `python myscript.py`
    - Submit `my_submit.slurm` to Slurm

4. While you can still run small scripts on the cluster without contacting Slurm, it's highly recommended to fully-tested your jobs on your PC or the workstation. Use the cluster only when you are ready to submit a large amount of computing work.
:::
    
#### b-2.1 Understand the cluster and Write Slurm script

We highly recommend going through the guide from Princeton Research Computing:
- https://researchcomputing.princeton.edu/get-started/guide-princeton-clusters
- https://researchcomputing.princeton.edu/support/knowledge-base/slurm
    
    
If you are impatient, you can directly jump to the Python page:
- https://researchcomputing.princeton.edu/support/knowledge-base/python


#### b-2.2 A helper tool for batch submitting jobs to the cluster

Before reading this section, be sure you understand the basics of a Slurm script (b-2.1).

To understand the use case of the helper tool, take our [Shelf 2D](https://github.com/YaoGroup/IceShelf2D) as example. We have a script file `script_inverse.py` for inversion of hardness. One can run the script via terminal:
```
python script_inverse.py 0.001 -o ./output_dir
```
where the number `0.001` specifies the noise ratio.

To systematically run the script with different noise ratios, using the terminal, one could do:
```
python script_inverse.py 0.001 -o ./noise_experiment &&
python script_inverse.py 0.002 -o ./noise_experiment &&
python script_inverse.py 0.005 -o ./noise_experiment &&
python script_inverse.py 0.01 -o ./noise_experiment &&
python script_inverse.py 0.02 -o ./noise_experiment &&
python script_inverse.py 0.05 -o ./noise_experiment &&
...
```
The above will run the script with different parameters, one after one (i.e. sequentially). To run the jobs parallelly on the cluster, we need to write a Slurm script using [job array](https://researchcomputing.princeton.edu/support/knowledge-base/slurm#arrays), which looks like (some details ommited):

```
#!/bin/bash
#SBATCH --job-name=test_sample 
#SBATCH --nodes=1 
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=1
#SBATCH --mem-per-cpu=4G
#SBATCH --time=0:30:43
#SBATCH --array=0-5

if [[ $SLURM_ARRAY_TASK_ID -eq "0" ]]; then python script_inverse.py 0.001 -o ./noise_experiment/0001
if [[ $SLURM_ARRAY_TASK_ID -eq "1" ]]; then python script_inverse.py 0.002 -o ./noise_experiment/0002
if [[ $SLURM_ARRAY_TASK_ID -eq "2" ]]; then python script_inverse.py 0.005 -o ./noise_experiment/0005
if [[ $SLURM_ARRAY_TASK_ID -eq "3" ]]; then python script_inverse.py 0.01 -o ./noise_experiment/001
if [[ $SLURM_ARRAY_TASK_ID -eq "4" ]]; then python script_inverse.py 0.02 -o ./noise_experiment/002
if [[ $SLURM_ARRAY_TASK_ID -eq "5" ]]; then python script_inverse.py 0.05 -o ./noise_experiment/005
```
    
We create a simple tool for precisely the above use case:
https://github.com/YaoGroup/slurm_tool

**As long as your script can vary the target variable by accepting argument(s) from terminal**, our tool can transform the above terminal task into a Slurm script for the cluster. For detailed usage, please refer to the GitHub page.

## C. Protect Your Data
    
:::info
To make sure we do not loss any important progress, it's our policy that:
* Upload all codes to GitHub
* Store all the data/documents on the cluster storage with backup system
:::

You already know how to upload code to GitHub. This section provides step-by-step guide on mounting data storage supported with backup system, provided by [Princeton Research Computing](https://researchcomputing.princeton.edu/support/knowledge-base/data-storage). Our group acquires few TB space on /projects/LAI. 

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

## D. Other References

### [Crash Course on Version Control using Git](https://hackmd.io/esQE9LzzTne-yhTrDzR9Iw?view)

### [Remote Access to the workstation](https://hackmd.io/9iVBJfITQwy8tIz9ubgorw?view)

### [Using Conda Environment Remotely with Visual Studio Code](https://hackmd.io/meeqtJktRfmAD-8gZwsk-g?view)
    
### [Jupyter with Environment File](https://hackmd.io/Cz7nFAVyTf-nx1WK6SrO-Q)
    
### [Scales-up PINN to Real Data (under construction)](https://hackmd.io/BLBm6v2CRHGe5xsfPGPN_g?view)
    
### [Della MATLAB GUI (under construction)](https://hackmd.io/i2ent7pRRGCYq8YR6Bk6aw)
