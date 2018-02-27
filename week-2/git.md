![git](images/git.jpg)

Git has exploded in popularity in recent years. The version control system is used by huge open source projects like Linux with thousands of contributors, teams of various sizes, solo developers and even  students.

## Getting Started - About Version Control

What is “version control”, and why should you care? Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later.

It allows you to revert selected files back to a previous state, revert the entire project back to a previous state, compare changes over time, see who last modified something that might be causing a problem, who introduced an issue and when, and more. Using a VCS also generally means that if you screw things up or lose files, you can easily recover. In addition, you get all this for very little overhead.



###  Local Version Control Systems

Many people’s version-control method of choice is to copy files into another directory,This approach is very common because it is so simple, but it is also incredibly error prone.
It is easy to forget which directory you’re in and accidentally write to the wrong file or copy over files you don’t mean to.

To deal with this issue, programmers long ago developed local VCSs that had a simple database that kept all the changes to files under revision control.

### Centralized Version Control Systems

The  major issue that people encounter is that they need to collaborate with developers on other systems. To deal with this problem, Centralized Version Control Systems (CVCSs) were developed.
These systems, such as CVS, Subversion, and Perforce, have a single server that contains all the versioned files, and a number of clients that check out files from that central place. 
For many years, this has been the standard for version control.

------

![centralized](images/centralized.png)

This setup offers many advantages, especially over local VCSs. For example, everyone knows to a certain degree what everyone else on the project is doing. Administrators have fine-grained control over who can do what, and it’s far easier to administer a CVCS than it is to deal with local databases on every client.However, this setup also has some serious downsides. The most obvious is the single point of failure that the centralized server represents. If that server goes down for an hour, then during that hour nobody can  collaborate at all or save versioned changes to anything they’re working  on.



### Distributed Version Control Systems

This is where Distributed Version Control Systems (DVCSs) step in. In a DVCS (such as Git, Mercurial, Bazaar or Darcs), clients don’t just  check out the latest snapshot of the files; rather, they fully mirror the repository, including its full history. Thus, if any server dies, and these systems were collaborating via that server, any of the client repositories can be copied back up to the server to restore it. Every clone is really a full backup of all the data.

![distributed](images/distributed.png)





### Getting Started - Git Basics

Git is a collection of command line utilities that track and record changes in files (most often source code, but you can track anything you wish). With it you can restore old versions of your project, compare,  analyze, merge changes and more. This process is referred to as **version control**

### The Three States

Git has three main states that your files can reside in: *committed*, *modified*, and *staged*:

- *Committed* means that the data is safely stored in your local database.
- *Modified* means that you have changed the file but have not committed it to your database yet.
- *Staged* means that you have marked a modified file in its current version to go into your next commit snapshot.

This leads us to the three main sections of a Git project: the Git directory, the working tree, and the staging area.

![](images/areas.png)



The **Git directory** is where Git stores the meta data and object database for your project.
This is the most important part of Git, and it is what is copied when you *clone* a repository from another computer.

**The working tree is a single** checkout of one version of the project.
These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.

**The staging area** is a file, generally contained in your Git directory, 
that stores information about what will go into your next commit.

The basic Git work flow goes something like this:

- You modify files in your working tree.
- You selectively stage just those changes you want to be part of your next commit, which adds *only* those changes to the staging area.
- You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.

### Installing on Windows

There are also a few ways to install Git on Windows.
The most official build is available for download on the Git website.
Just go to [http://git-scm.com/download/win]() and the download will start automatically.
Note that this is a project called Git for Windows, which is separate from Git itself; for more information on it, go to [ https://git-for-windows.github.io/]() .

## First-Time Git Setup

The first thing you should do when you install Git is to set your user name and email address.
This is important because every Git commit uses this information, and it’s immutably baked into the commits you start creating

```bash
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

### Getting a Git Repository

You typically obtain a Git repository in one of two ways:

1. You can take a local directory that is currently not under version control, and turn it into a Git repository, or
2. You can *clone* an existing Git repository from elsewhere

### Initializing a Repository in an Existing Directory

If you have a project directory that is currently not under version  control and you want to start controlling it with Git, you first need to go to that project’s directory.

for Windows:

```basic
 cd /c/user/my_project
```

and type:

```bash
git init
```

This creates a new subdirectory named `.git` that contains all of your necessary repository files  a Git repository skeleton.  At this point, nothing in your project is tracked yet.

f you want to start version-controlling existing files (as opposed to an
 empty directory), you should probably begin tracking those files and do
 an initial commit.
You can accomplish that with a few `git add` commands that specify the files you want to track, followed by a `git commit`:

```bash
$ git add *.c
$ git add LICENSE
$ git commit -m 'initial project version'
```



### Cloning an Existing Repository

If you want to get a copy of an existing Git repository — for example, a
 project you’d like to contribute to — the command you need is `git clone`.

```bash
git clone https://github.com/libgit2/libgit2
```

That creates a directory named `libgit2`, initializes a `.git` directory inside it, pulls down all the data for that repository, and checks out a working copy of the latest version.
If you go into the new `libgit2` directory that was just created, you’ll see the project files in there, ready to be worked on or used.



### Recording Changes to the Repository

 Each file in your working directory can be in one of two states: *tracked* or *untracked*. **Tracked files** are files that were in the last snapshot; they can be unmodified, modified, or staged. In short, tracked files are files that Git knows about.

**Untracked files** are everything else — any files in your working directory that were not in your last snapshot and are not in your staging area. When you first clone a repository, all of your files will be tracked and unmodified because Git just checked them out and you haven’t edited anything.

As you edit files, Git sees them as modified, because you’ve changed them since your last commit. As you work, you selectively stage these modified files and then commit all those staged changes, and the cycle repeats.

### Checking the Status of Your Files

The main tool you use to determine which files are in which state is the **git status** command. If you run this command directly after a clone, you should see something like this:

```bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```

This means you have a clean working directory — in other words, none of your tracked files are modified. Git also doesn’t see any untracked files, or they would be listed here. Finally, the command tells you which branch you’re on and informs you that it has not diverged from the same branch on the server.



Let’s say you add a new file to your project, a simple `README` file. If the file didn’t exist before, and you run `git status`, you see your untracked file like so:

```bash
git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    README

nothing added to commit but untracked files present (use "git add" to track)
```

You can see that your new `README` file is untracked, because it’s under the “Untracked files” heading in your status output. Untracked basically means that Git sees a file you didn’t have in the previous snapshot (commit).

### Tracking New Files

In order to begin tracking a new file, you use the command `git add`. To begin tracking the `README` file, you can run this:

```bash
$ git add README
```

If you run your status command again, you can see that your `README` file is now tracked and staged to be committed:

```bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README
```

### Staging Modified Files

Let’s change a file that was already tracked. If you change a previously tracked file called `CONTRIBUTING.md` and then run your `git status` command again, you get something that looks like this:

```bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
```

The `CONTRIBUTING.md` file appears under a section named “Changes not staged for commit” — which means that a file that is tracked has been modified in the working directory but not yet staged. To stage it, you run the `git add` command. `git add` is a multipurpose command — you use it to begin tracking new files, to stage files, and to do other things like marking merge-conflicted files as resolved.

### Ignoring Files

Often, you’ll have a class of files that you don’t want Git to automatically add or even show you as being untracked. These are generally automatically generated files such as log files or files produced by your build system. In such cases, you can create a file listing patterns to match them named `.gitignore`. Here is an example `.gitignore` file:

```bash
$ cat .gitignore
*.[oa]

```

The first line tells Git to ignore any files ending in “.o” or “.a” — object and archive files that may be the product of building your code.



### Committing Your Changes

Now that your staging area is set up the way you want it, you can commit your changes. Remember that anything that is still unstaged — any files you have created or modified that you haven’t run `git add` on since you edited them — won’t go into this commit. They will stay as modified files on your disk. In this case, let’s say that the last time you ran `git status`, you saw that everything was staged, so you’re ready to commit your changes. The simplest way to commit is to type `git commit -m "Story 182: Fix benchmarks for speed`:

Remember that the commit records the snapshot you set up in your staging area. Anything you didn’t stage is still sitting there modified; you can do another commit to add it to your history. Every time you perform a commit, you’re recording a snapshot of your project that you can revert to or compare to later.

### Removing File

To remove a file from Git, you have to remove it from your tracked files (more accurately, remove it from your staging area) and then commit. The `git rm` command does that, and also removes the file from your working directory so you don’t see it as an untracked file the next time around.

If you simply remove the file from your working directory, it shows up under the “Changes not staged for commit” (that is, *unstaged*) area of your `git status` output:

```bash
$ rm PROJECTS.md
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        deleted:    PROJECTS.md

no changes added to commit (use "git add" and/or "git commit -a")
```

