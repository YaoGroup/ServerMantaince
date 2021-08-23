Yao Group Workstation Infrastructure Note
---

[View it on HackMD](https://hackmd.io/dd8wi827SpCLAe8p2Ype6w)

This note serves for the following purpose:
- As the on-board training for anyone using the workstation for their work. Best practice for writing code and using workstation to run their code.
- As the reference note for basic technical issues, or additional tips for enhance the personal workflow.
- As the reference note for future administrator to understand the system set-up.

The note is the main page, and contains links to additonal references. The main page aims at on-board new comber, so they can grasp the essentail concept and start using workstation ASAP. Additional references teach one how to achieve specific things, in step-by-step way.

:::info
Before you started, check you already get a account and a preset password for the workstation.
And if you are outside Princeton, make sure you are using VPN.
:::

## Login To the Server

Open a terminal. On Windows, one can use [PowerShell](https://www.howtogeek.com/662611/9-ways-to-open-powershell-in-windows-10/). On Mac, one can open the [native terminal](https://www.howtogeek.com/682770/how-to-open-the-terminal-on-a-mac/)

Type the following into terminal, then press enter:
`ssh <your_account_name>@yaolab.princeton.edu`

Then it will ask for password, type the one you get from Yao, then you should successfully login into the workstation.

## A. The Basics

We start by introducing the basic concpet and workflow for using the workstation. After reading through A-1 to A-3, one should able to start working on workstation. We hope the best practices can be followed, while remains the tutorial consice enough so everyone quickly start enjoying their research work.

### A-1 Embrace the Command Line

Use text to control a computer is still the most robust and effective way to use a computer. We want to ensure everyone is able to use the workstation with text-based command in command line.


#### a-1.1 Understand what you see

After login, you shall see:
![](https://i.imgur.com/3BcqlE3.png)

:::success
After the unimportant welcom message, there are two important elements on the screen

* **Username**: The `mc4536` indicates my user name. For you, it will be your account name.

* **Current Directory**: The text between the colon `:` and number sign `#`, in this case it's the tilde `~`, indicated **where you are** on the computer (the formal name for this is *current working directory*).

$\small\text{Note that on a different machine, the colon or the number sign can become something else}$
:::

#### a-1.2 Execute Command

Type `passwd` to the screen then press enter, it will be the very first command you type.
It's a command to change your password. Follow the instructions and set a one you like.

Now will give it second shot. But this time, only type `passw` and execute. You'll get the followings. You can see that the system is smart. When you type a non-existing command, it will try finding some suggestions. When you forgot a command, you may find the suggestions helpful:\
![](https://i.imgur.com/o9TROVr.png)

Now we do it third time. This time, we type `pas`, then **click the Tab twice**, you shall see:
![](https://i.imgur.com/gmCarwM.png)

The **Tab** key is a killer feature for command line. If you type something with correct prefix, it will try to complete the rest. If multiple results matches, click Tab twice will display them all. It saves time for typing, and the burden to remeber things.

:::success
Rule of thumb: **No need to remember command.**

You'll remember them automatically after doing it hundreds of times. Before that, find some suggestion from the system, use Tab, or google.
:::

#### a-1.3 Understand the Working Directory
![](https://i.imgur.com/aNrTKnV.png)\
[Photo credit: TecMint](https://www.tecmint.com/linux-directory-structure-and-important-files-paths-explained/)

The linux directory is a [Tree](https://en.wikipedia.org/wiki/Tree_(data_structure)). The directories are separated by slash `/`. The root of the directory system has no name, so the path of the root is simply a single slash: `/`. There are many directories under root, we now only focus on a directory called **home**. The path to that directory is thus `/home`. Under home, there multiple directories, one for each user. We'll see that in short.

When you are on the workstation, at anytime you must be inside one of the directory, which is called **current working directory**. By default, after login, you are on a directory `~`, which seems strange and violates what we said about slash and directory names. Actually, tilde `~` is a shortened form for the directory `/home/<your user name>`, thus is different for every user. For example, for me, `~` means `/home/mc4536` actually.

`pwd` displays where you are. It displays the full path, instead of using abbreviated tilde `~`:\
![](https://i.imgur.com/AmFe1Ou.png)

:::success
We call the directory `/home/<your user name>` simply **home**, **home directory** or **user's home**. Everyone has its own home directory. We seldom need to use `/home` thus no need another name for that.
:::


#### a-1.4 Basic Command

We introduce the 7 essential commands:

:::info
**Switch your working directory:**

**`cd <target directory>`**

You see that the location after you name changes.\
You can also confirm that by using `pwd`
:::

:::info
**List files/directories under a directory:**\
**`ls <target directory>`**
<br></br>
Also, the file names starting with preiod `.` is considered hidden. `ls` will not display them by default. One can display hidden files by adding `-a` before `<target directory>`\
![](https://i.imgur.com/ySVoiev.png)

There are quite a few hidden files under users' home.
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
`mkdir -p /a/series/of/directory/`
:::

:::warning
**Edit a Text File**\
`vim <target for edit>`
<br></br>
Tougher. Under construction.
:::

:::info
**Upload/Download File from Workstation**
<br></br>
Upload from the local PC to the workstation:\
`scp -r D:\what\I\want\to\upload <my-account>@yaolab.princeton.edu:/place/to/upload/`
<br></br>
Download from the workstation to the local PC -- just reverse the arguments of upload:\
`scp -r <my-account>@yaolab.princeton.edu:/target/to/download/ D:\where\I\want\to\store`
:::

By combining the above commands, you can conduct all essentials on the workstation.

### A-2 Version Control Tool (Git)

Git is the powerful verson control system. In this short tutorial, we'll introduce concepts of version control and the basic usage of Git.After go through the tutorial, you will be able to properly use eseentail features of Git. 

Before we start, you need to create a empty directory and follow te instruction of the tutorial. I use `~/Document/git-test` as example.
Now Execute: `git init`

The command will create a hidden directory `.git` under current working directory:
![](https://i.imgur.com/S5D9lcD.png)

Git stores almost everything it needs for controlling a project under the `.git` folder. Be careful not to remove or modify anything inside it, if you don't know how it works internally. You may destroy the critial data for version control.

#### a-2.1 Your First Commit

The fundamental element of a version control system, is a save point. Save point means a snapshot of what files are like at the time of saving.In Git, we call a save point **commit**. Also when we use commit as verb, for storing files into a commit.

:::info
Using Git is essentially creating a series of commits, one after one, to form a history of commits. Git call a history of commit **repository**.
:::

Now we are going to add the first point of our new history.
We create a file called *my-first-file.py*, with only a simple line "Hello World!":
![](https://i.imgur.com/lehHrPj.png)

We now check the status of our repository by `git status`
![](https://i.imgur.com/YUIO8jG.png)

It's acutally self-explaining. It says that there is a new file *my-first-file.py* not tracked by Git. The first step of committing, is to add the file(s) you want to commit. Do it by `git add my-first-file.py`:
![](https://i.imgur.com/HQy5yVV.png)

Now it says we are ready to commit a change, which is the new file we created.\
We commit it by `git commit`. It will open a editor to type some consice and meaningful message.\
We type `The very first commit` here.
![](https://i.imgur.com/XTmSx4R.png)

Then we can check the history of commits by `git log`. It says that we have a commit, with the ID `4e0846d1e2fd8dc54b17c734f8df6b2863106051` and message `The very first commit`.
![](https://i.imgur.com/evEM2zW.png)

Using `git log --oneline --graph` one can display the commit history consicely. The `HEAD` is where we are currently.
![](https://i.imgur.com/dDRCnNO.png)

:::success
**Takeaway**
* `git status` is the main way to examine the un-commited changes.
* `git add` is for gathering the changes for a upcomming action to commit.
* `git commit` creates a commit of all the gathered changes, and add the commit into history.
* `git log` are the main way to examine the history of commits.
:::

#### a-2.2 Travel in History

We modify the `my-first-file.py` to see how future changes form the history.
First we modify the file by:
* Remove the `Hello World` line
* Add a new line `print("Hello world!")`
* Use `git status` to check the changes
* Use `git diff` to view the changes line by line
![](https://i.imgur.com/XEYXmOE.png)

From the outputs of `git status`, we see that Git knows there are changes for a file in track.\
`git diff` further display the changes. The minus sign - means the line is deleted and plus sign + means the line is added:
```
-Hello World!
+print("Hello World!")
```

We then add & commit the changes, and view the history. One can see that there are two commits: the first one we added in [a-2.1](https://hackmd.io/dd8wi827SpCLAe8p2Ype6w?view#a-21-Your-First-Commit), and after which is the `print("Hello World")` one.
![](https://i.imgur.com/48zh7L5.png)

We could use `git show` to display the changes of last commit:
![](https://i.imgur.com/BgBYO34.png)

Now we teach you how to do time travel -- go back to the state of a commit in history:\
`git checkout 4e0846`

Note that `4e0846` is the first digits of ID of the first commit. Your ID will be different than mine.
Now we check the content of the file, we see that it's back to the first committed version:
![](https://i.imgur.com/Ctc2qgv.png)

Switch back to the lasted commit, again by `git checkout <commit id>` and view the content of the `my-first-file.py`:
![](https://i.imgur.com/GPcBhvA.png)

:::success
**Takeaway**
* Commit stacks one after another (along a branch, see a-2.2).
* Changes in file are represented by "-" and "+" of lines.
* `git diff` displays all the un-added and un-committed changes.
* `git show` display the detailed changes of last commit.
* `git checkout <commit id>` **in-place** modify the content of files to the state of a commit in history
:::

#### a-2.2 Branch
At some point of the project, you'll need different versions of the project. Maybe there are diverged directions about the project. Maybe you want to experiment a change, but not yet determine the changes should for everyone involved. The plain old way of doing this is copying the entire directory. I hope you stop doing this after reading this section:
![](https://i.imgur.com/edWDdw4.png)

For example, we want to expriment to print *Hello World* multiple times, but not sure if everyone needs this change. We can still do it within the sample repository. To this point, our history is a single series of commits, one after another. Now we are going for seperated the change from "main history".

We create a new branch *experiment* by `git branch experiment`.\
We check the status by `git branch`:\
The star "*" before the *main* indicates we are still at *main* branch.\
![](https://i.imgur.com/fKXK8EB.png)

Now we switch to the *expriment* branch by `git checkout experimnet`\
![](https://i.imgur.com/75nVaQQ.png)

**Now we demonstate the ability of Git to diverge the history**. First add a commit when we are in *experiment branch*. Then we switch back to *main branch* and add a new commit there. 
![](https://i.imgur.com/8Yq3HKQ.png)

Then use `git log --all --oneline --graph` to view the history. You see that we add two commits, which are separated from the `bfc86c5` commit.
![](https://i.imgur.com/c0LE9hk.png)

:::success
We highly encourage you to play the above yourself. 

Examine the content of files and commit history during the process.

That's the fastest way to grasp the concept and rationalize what you see.
:::


#### a-2.3 Interact with Remote
...

### A-3 Python Environment
...

## B. Enhanced Workflow

We provide some useful additional tricks for using the workstation. The tricks can:
- Smooth and boost tedious routines
- Enhance the robustness of the workflow against human error
...

### B-1 To Automate Everything (Shell Configuration)
...
...
...

### B-2 Secure Your Long-Running Jobs
...
...
...

### B-3 More Version Control
...
...
...

## C. References

### [Remote Access to the workstation](https://hackmd.io/@MingRuey/r1LzVB3lY)

### [Using Conda Environment](https://hackmd.io/@MingRuey/ryZtHShlF)

### [Using Long-term Storage on HPC](https://hackmd.io/@MingRuey/HJjXIr2xF)
