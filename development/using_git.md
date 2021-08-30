# Creash Course on Version Control using Git

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

## Your First Commit

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

## Travel in the History of Code

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

## New Branch for Managing Multiple Versions
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

## Interact with GitHub

We demonstrate how to use Git to interact with GitHub.

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
Git needs to know how to **map a local branch to a remote branch** for uploading. It's a good practice to make the name of the local branch the same as a remote one.
:::

:::info
**Download the Commits from Remote**

`git pull`

or if local has un-uploaded commits **and** remote has new commit(s) uploaded by other team members

`git pull --rebase`\
\
Git needs to resolve how to combine the local (un-uploaded) changes with the new remote changes if both exist. **Option --rebase** is a way to handle the issue. It will find and start with the most recent common commits, apply the remote commits first, then apply the local ones.
:::