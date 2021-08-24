Yao Group Workstation Infrastructure Note
---

[View it on HackMD](https://hackmd.io/dd8wi827SpCLAe8p2Ype6w)

This note serves the following purpose:
- As the onboard training for anyone using the workstation for his work. It provides best practices for writing code and using the workstation to run code.
- As the reference note for fundamental technical issues or additional tips for enhancing the personal workflow.
- As the reference note for the future administrator to understand the system set-up.

The note is the main page and contains links to additional references. The main page aims at onboard new comber, so they can grasp the essential concepts and start using the workstation ASAP. Other references teach one how to achieve specific things in a step-by-step way.

:::info
Before you started, check you already get an account and a reset password for the workstation.
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

We start by introducing the basic concept and workflow for using the workstation. After reading through A-1 to A-3, one should be able to start working on the workstation. We hope the tutorial is concise, so everyone quickly starts enjoying their research work while following the best practice.

### A-1 Embrace the Command Line

Use text to control a computer is still the most robust and effective way to use a computer. We want to ensure everyone can use the workstation with text-based commands in the command line.


#### a-1.1 Know Your Home

After login, you shall see:
![](https://i.imgur.com/3BcqlE3.png)

:::info
After the unimportant welcome message, there are two important elements on the screen.

* **username**: The `mc4536` indicates my user name. For you, it will be your account name.
* **Current Directory**: The text between the colon `:` and number sign `#`, in this case, it's the tilde `~`, indicated **where you are** on the computer (the formal name for this is *current working directory*).

$\small\text{^On a different machine, the colon or the number sign can become something else}$
:::

All files and directory in Linux forms a [Tree](https://en.wikipedia.org/wiki/Tree_(data_structure)). The slash `/` separates the names of directories and files. The root of the directory system has no name, so the root path is simply a single slash: `/`. There are many directories under root; we now only focus on a directory called **home**. The path to that directory is thus `/home`. Under home, there are multiple directories, one for each user. We'll see that in short.

:::info
There is no apparent difference between a file and a directory. For example, given a path, `/home/mc4536/Conda`, one can not tell if it is a file or directory. The fundamental difference between the two is that a directory can contain files but not vice versa.
:::

![](https://i.imgur.com/aNrTKnV.png)\
[Photo credit: TecMint](https://www.tecmint.com/linux-directory-structure-and-important-files-paths-explained/)

When you are on the workstation, at any time, you must be inside one of the directories, which is called **current working directory**. By default, after login, you are on a directory tilde `~`. Tilde `~` is a shortened form for the directory `/home/<your user name>`; this is different for every user. For example, for me, `~` means `/home/mc4536` actually.

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

We introduce the seven essential commands:

:::info
**Switch your working directory:**

**`cd <target directory>`**

You see that the location after your name changes.\
You can also confirm that by using `pwd`
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

Version control means managing the changes of files in an organized way. Version control tool is the software to aid the process.

In this short tutorial, we'll introduce concepts of version control and the primary usage of Git. Going through the tutorial, you will be able to properly manage code using the essential features of Git.

Before we start, you need to create an empty directory and transform it into a Git-managed project. I use `~/Document/git-test` as an example.

Inside the directory, execute: `git init

The command will create a hidden directory `.git` under the current working directory:
![](https://i.imgur.com/S5D9lcD.png)

Git will monitor the files under the directory. The directory is now the place for you to start working. Put your work under the directory and use Git to control it.

:::success
[Our recording for a teaching session](https://princeton.zoom.us/rec/share/G-pdNxvmzI7aAewSKjSCjPxXjDyNjiLYVEGzMdUjrSgxr4tzE0gxZ6pQgCoIK1ZQ.D5mzb9Nu_jWZZBLU) may help you also.
:::

$\small\text{^Git stores almost everything it needs under the .git folder.}$
$\small\text{Be careful not to remove or modify anything inside it if you don't know how it works internally.}$

#### a-2.1 Your First Commit

The fundamental element of a version control system is a save point. Savepoint means a snapshot of what files are like at the time of saving. In Git, we call a savepoint **commit**. Also, when we use commit as a verb, it means storing changes into a commit.

:::info
Using Git is essentially creating a series of commits, one after one, to form a history of commits. Git call history of commits **repository**.
:::

Now we are going to add the first point of our new history.
We create a file called *my-first-file.py*, with only a simple line "Hello World!":
![](https://i.imgur.com/lehHrPj.png)

We now check the status of our repository by `git status
![](https://i.imgur.com/YUIO8jG.png)

The message is self-explaining. It says that there is a new file *my-first-file.py* not tracked by Git. The first step of committing is to add the file(s) you want to commit. Do it by `git add my-first-file.py`:
![](https://i.imgur.com/HQy5yVV.png)

Now it says we are ready to commit a change, which is the new file we created.\
We commit it by `git commit`. It will open an editor for you to type some concise and meaningful message. Our message here is `The very first commit`.

Then we can check the history of commits by `git log`. It says that we have a commit, with the ID `4e0846d1e2fd8dc54b17c734f8df6b2863106051` and message `The very first commit`.
![](https://i.imgur.com/evEM2zW.png)

:::success
**Takeaway**
* `git status` is the main way to examine the un-committed changes.
* `git add` is for gathering the changes for an upcoming action to commit.
* `git commit` creates a commit of all the gathered changes and adds the commit into history.
* `git log` are the primary way to examine the history of commits.
:::

#### a-2.2 Travel in the History of Code

We modify the `my-first-file.py` to see how the future changes create a history.
First, we modify the file by:
* Remove the `Hello World` line
* Add a new line `print("Hello world!")`
* Use `git status to check the changes
* Use `git diff` to view the changes line by line
![](https://i.imgur.com/XEYXmOE.png)

From the outputs of `git status, we see that Git knows there are changes for a tracked file.
Use `git diff` to display the (uncommitted) changes. The sign - means the lines are deleted, and sign + means the lines are added:
```
-Hello World!
+print("Hello World!")
```

We then add & commit the changes and view the history. One can see that there are two commits: the first one we added in [a-2.1](https://hackmd.io/dd8wi827SpCLAe8p2Ype6w?view#a-21-Your-First-Commit), and after which is the `print("Hello World")` one.
![](https://i.imgur.com/48zh7L5.png)

Using `git log --online --graph`, one can display the commit history concisely. The `HEAD` is where we are currently.
![](https://i.imgur.com/dDRCnNO.png)

We could use `git show` to display the changes of the last commit:
![](https://i.imgur.com/BgBYO34.png)

Now we teach you how to do time travel -- go back to the state of a commit in history:\
`git checkout 4e0846`

Note that `4e0846` is the first few digits of the ID of the first commit. Your ID will be different than mine.
Now we check the content of the file and see that it's back to the first committed version:
![](https://i.imgur.com/Ctc2qgv.png)

Switch back to the lasted commit, again by `git checkout <commit id>` and view the content of the `my-first-file.py`:
![](https://i.imgur.com/GPcBhvA.png)

:::success
As you see, once you commit the code, Git remembers what the code currently is. You can switch back to the previous version at will. **The entire history of changes is managed under a single directory.** Code management becomes clean and systematic.
:::

:::success
**Takeaway**
* Commit your work and feel free to modify the code further.
* `git diff` displays all the un-added and un-committed changes.
* `git show` displays the detailed changes of the last commit.
* `git checkout <commit id>` **in-place** modify the content of files to the state of a commit in history
:::

#### a-2.3 New Branch for Managing Multiple Versions
At some point in the project, you'll need different versions of the project. Maybe there are diverged directions about the project. Perhaps you want to experiment with a change but not yet determine everyone should use the changes.

The plain old way of doing this:
![](https://i.imgur.com/tgTGuAw.png)

After reading the section, I hope you find Git has a far better way to solve the problem.

For example, we want to print *Hello World* multiple times, but we are not sure if everyone needs this change. We can still do it within the same repository. To this point, our history is a single series of commits, one after another. Now we are going to separate the change from the "main history".

We create a new branch *experiment* by `git branch experiment`.\
We check the status by `git branch`:\
The star "*" before the *main* indicates we are still at the *main* branch.\
![](https://i.imgur.com/fKXK8EB.png)

Now we switch to the *experiment* branch by `git checkout experiment\
![](https://i.imgur.com/75nVaQQ.png)

**Now, we demonstrate the ability of Git to bifurcate the project**. We do not go through the steps here. But they are conceptually simple:
* Add a commit when we are in the *experiment* branch.
* Switch to *main* branch 
* Add a commit when we are in *main* branch

Then use `git log --all --online --graph` to view the history. You see that we add two commits, separating from the `bfc86c5` commit.
![](https://i.imgur.com/c0LE9hk.png)

:::success
"Splitting" the project by using multiple branches is powerful. All within a single repository, one can **easily manage multiple versions, especially when they are not necessary older/newer than others.**

We highly encourage you to play above yourself. Examine the content of files and commit history during the process. That's the fastest way to grasp the concept and rationalize what you see.
:::


#### a-2.4 Sharing the Code

We use [GitHub](https://github.com/) as the platform for collaboratively working on projects. GitHub, as its name suggested, is tightly integrated with Git. We demonstrate how to use Git to interact with GitHub.

We start by opening a new project on GitHub:
* Open [Github](https://github.com/)
* Register an account if you don't have one
* Open a new repository by clicking the plus "+" sign on the top right and select "New Repository"
* Select a name you like. Here we use "TutorialOnGit"
* The rest boxes could remain unchecked

![](https://i.imgur.com/sFqFX48.png)

Now comes the fundamental concept of interacting with GitHub.

:::info
GitHub stores a repository on its own. It is called **remote repository**.\
\
The repository we work from a-2.1 to a-2.3 is called **local repository** in this context. "Local" emphasizes that the repository resides on a local computer.\
\
Team members are working on their local repositories on their computer, while **share their local histories across the team through synchronization with a remote repository.**
:::

In the following, we show how to wire your local history to the remote one. First, we need to register a remote repository for a local one.

The command `git remote` displays the list of repositories, currently empty, since there is none. We add one by:

`git remote add <a name you like> <your remote repo link>`

You can choose a name you like for the remote repository. "origin" is typical. One can find the link for the remote repository on the project page:

![](https://i.imgur.com/z8KIk01.png)

In this case, we do
* `git remote add origin https://github.com/MingRuey/TutorialOnGit.git` 
* Check `git remote` display `origin`, which we just added
* Check `git remote get-URL origin` displays the address of origin (`https://github.com/MingRuey/TutorialOnGit.git`)

Now, we are ready for synchronization with this GitHub remote repository. There are just basically two things -- upload and download commits.

:::info
**Upload All Local Commits in a Branch to the Remote**

`git push`

or if first time uploading a branch

`git push --set-upstream origin <branch>`
\
\
Git needs to know how to **map a local branch to a remote branch** for uploading. It's a good practice to make the name of the local branch exactly the same as a remote one.
:::

:::info
**Download the Commits from Remote**

`git pull`

or if local has un-uploaded commits **and** remote has new commit(s) uploaded by other team members

`git pull --rebase`\
\
Git needs to resolve how to combine the local (un-uploaded) changes with the new remote changes if both exist. **Option --rebase** is a way to handle the issue. It will find and start with the most recent common commits, apply the remote commits first, then apply the local ones.
:::


### A-3 Setup Environment and Using Python
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
