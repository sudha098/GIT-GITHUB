# GIT-GITHUB


Using Git with Command Line
---------------------------
The first thing we need to do, is to check if Git is properly installed:
git --version

Configure Git
-------------
Now let Git know who you are. This is important for version control systems, as each Git commit uses this information:

git config --global user.name "John Doe"

git config --global user.email "John@abc.com"

Change the user name and e-mail address to your own. You will probably also want to use this when registering to GitHub later on.

Note: Use global to set the username and e-mail for every repository on your computer.
-----
If you want to set the username/e-mail for just the current repo, you can remove global

Creating Git Folder
-------------------
Now, let's create a new folder for our project:

mkdir myproject

cd myproject

git init 

Git Adding New Files
--------------------

You just created your first local Git repo. But it is empty.
So add some files, or create a new file using your favourite text editor. Then save or move it to the folder you just created.

git status

Now Git is aware of the file, but has not added it to our repository!

Files in your Git repository folder can be in one of 2 states:

1. Tracked - files that Git knows about and are added to the repository
2. Untracked - files that are in your working directory, but not added to the repository
 When you first add files to an empty repository, they are all untracked. To get Git to track them, you need to stage them, or add them to the staging environment.

Git Staging Environment
-----------------------

One of the core functions of Git is the concepts of the Staging Environment, and the Commit.

As you are working, you may be adding, editing and removing files. But whenever you hit a milestone or finish a part of the work, you should add the files to a Staging Environment.
Staged files are files that are ready to be committed to the repository you are working on. You will learn more about commit shortly.

For now, we are done working with index.html. So we can add it to the Staging Environment:

git add index.html

The file should be Staged. Let's check the status::

git status


Git Commit
----------

Since we have finished our work, we are ready move from stage to commit for our repo.

Adding commits keep track of our progress and changes as we work. Git considers each commit change point or "save point". It is a point in the project you can go back to if you find a bug, or want to make a change.

When we commit, we should always include a message.

By adding clear messages to each commit, it is easy for yourself (and others) to see what has changed and when.

git commit -m "First commit"

The commit command performs a commit, and the -m "message" adds a message.

The Staging Environment has been committed to our repo, with the message:
"First release of Hello World!"

Git Commit without Stage
------------------------

Sometimes, when you make small changes, using the staging environment seems like a waste of time. It is possible to commit changes directly, skipping the staging environment. The -a option will automatically stage every changed, already tracked file.

git commit -a -m "Updated index.html with a new line"

And check the status of our repository. But this time, we will use the --short option to see the changes in a more compact way:
git status --short

Git Commit Log
--------------
To view the history of commits for a repository, you can use the log command:

git log

Git Help
--------
If you are having trouble remembering commands or options for commands, you can use Git help.

There are a couple of different ways you can use the help command in command line:

git command -help -  See all the available options for the specific command
git help --all -  See all possible commands
 Let's go over the different commands.

Git Branch
----------
Working with Git Branches

In Git, a branch is a new/separate version of the main repository.

Let's say you have a large project, and you need to update the design on it.

How would that work without and with Git:

Without Git:

1. Make copies of all the relevant files to avoid impacting the live version
2. Start working with the design and find that code depend on code in other files, that also need to be changed!
3. Make copies of the dependant files as well. Making sure that every file dependency references the correct file name
4. EMERGENCY! There is an unrelated error somewhere else in the project that needs to be fixed ASAP!
5. Save all your files, making a note of the names of the copies you were working on
6. Work on the unrelated error and update the code to fix it
7. Go back to the design, and finish the work there
8. Copy the code or rename the files, so the updated design is on the live version
9. (2 weeks later, you realize that the unrelated error was not fixed in the new design version because you copied the files before the fix)

With Git:

1. With a new branch called new-design, edit the code directly without impacting the main branch
2. EMERGENCY! There is an unrelated error somewhere else in the project that needs to be fixed ASAP!
3. Create a new branch from the main project called small-error-fix
4. Fix the unrelated error and merge the small-error-fix branch with the main branch
5. You go back to the new-design branch, and finish the work there
6. Merge the new-design branch with main (getting alerted to the small error fix that you were missing)
7. Branches allow you to work on different parts of a project without impacting the main branch.

When the work is complete, a branch can be merged with the main project.

You can even switch between branches and work on different projects without them interfering with each other.

Branching in Git is very lightweight and fast!

New Git Branch
--------------
Let add some new features to our index.html page.

We are working in our local repository, and we do not want to disturb or possibly wreck the main project.

So we create a new branch:
        git branch development
Now we created a new branch called "development"

Let's confirm that we have created a new branch: 
        git branch

checkout is the command used to check out a branch. Moving us from the current branch, to the one specified at the end of the command:
        git checkout development

Note: Using the -b option on checkout will create a new branch, and move to it, if it does not exist

Switching Between Branches
--------------------------

git checkout master

Git Branch Merge
----------------

git checkout master

Now we merge the current branch (master) with development:
git merge development

#Push Local Repository to GitHub
--------------------------------
git remote add origin https://github.com/sudha098/GIT-GITHUB.git

git remote add origin URL specifies that you are adding a remote repository, with the specified URL, as an origin to your local Git repo.

Now we are going to push our master branch to the origin url, and set it as the default remote branch:

git push --set-upstream origin master

Note: Since this is the first time you are connecting to GitHub, you will get some kind of notification you to authenticate this connection

Git Pull from GitHub
--------------------

Pulling to Keep up-to-date with Changes
When working as a team on a project, it is important that everyone stays up to date.

Any time you start working on a project, you should get the most recent changes to your local copy.

With Git, you can do that with pull.

pull is a combination of 2 different commands:

1. fetch
2. merge
Let's take a closer look into how fetch, merge, and pull works.

Git Fetch
----------
fetch gets all the change history of a tracked branch/repo.

So, on your local Git, fetch updates to see what has changed on GitHub:

git fetch origin

Now that we have the recent changes, we can check our status:
    git status
We are behind the origin/master by 1 commit. That should be the updated README.md, but lets double check by viewing the log: git log origin/master
That looks as expected, but we can also verify by showing the differences between our local master and origin/master:
    git diff origin/master
That looks precisely as expected! Now we can safely merge.

Git Merge
---------
merge combines the current branch, with a specified branch.

We have confirmed that the updates are as expected, and we can merge our current branch (master) with origin/master:

git merge origin/master

Git Pull
--------
But what if you just want to update your local repository, without going through all those steps?

pull is a combination of fetch and merge. It is used to pull all changes from a remote repository into the branch you are working on.

Make another change to the Readme.md file on GitHub.

Use pull to update our local Git:
    git pull origin

# Git GitHub Fork

Add to Someone Else's Repository
--------------------------------

At the heart of Git is collaboration. However, Git does not allow you to add code to someone else's repository without access rights.

In these next 3 chapters we will show you how to copy a repository, make changes to it, and suggest those changes be implemented to the original repository.

Fork a Repository
------------------
A fork is a copy of a repository. This is useful when you want to contribute to someone else's project or start your own project based on theirs.

fork is not a command in Git, but something offered in GitHub and other repository hosts. Let's start by logging in to GitHub, and fork our repository:
    https://github.com/sudha098/GIT-GITHUB.github.io

Configuring Remotes
-------------------
Basically, we have a full copy of a repository, whose origin we are not allowed to make changes to.

Let's see how the remotes of this Git is set up:
git remote -v

We see that origin is set up to the original "w3schools-test" repository, we also want to add our own fork.

First, we rename the original origin remote:

Example
git remote rename origin upstream
git remote -v

Then fetch the URL of our own fork:
And add that as origin:
git remote add origin https://github.com/sudha098/GIT-GITHUB.github.git
git remote -v


Note: According to Git naming conventions, it is recommended to name your own repository origin, and the one you forked for upstream

Now we have 2 remotes:

origin - our own fork, where we have read and write access
upstream - the original, where we have read-only access

# Git Revert
------------

revert is the command we use when we want to take a previous commit and add it as a new commit, keeping the log intact.

Step 1: Find the previous commit:

Step 2: Use it to make a new commit:

Let's make a new commit, where we have "accidentally" deleted a file:

Now we have a part in our commit history we want to go back to. Let's try and do that with revert.

Git Revert Find Commit in Log
-----------------------------
First thing, we need to find the point we want to return to. To do that, we need to go through the log.

To avoid the very long log list, we are going to use the --oneline option, which gives just one line per commit showing:

The first seven characters of the commit hash
the commit message
So let's find the point we want to revert:
git log --oneline

Git Revert HEAD
---------------
We revert the latest commit using git revert HEAD (revert the latest change,  and then commit), adding the option --no-edit to skip the commit message editor (getting the default revert message):

Example
git revert HEAD --no-edit

Now let's check the log again:

Example
git log --oneline

Note: To revert to earlier commits, use git revert HEAD~x (x being a number. 1 going back one more, 2 going back two more, etc.)

# GIT RESET
-----------

Git Reset
reset is the command we use when we want to move the repository back to a previous commit, discarding any changes made after that commit.

Step 1: Find the previous commit
Step 2: Move the repository back to that step

Git Reset Find Commit in Log

First thing, we need to find the point we want to return to. To do that, we need to go through the log.

To avoid the very long log list, we are going to use the --oneline option, which gives just one line per commit showing:

The first seven characters of the commit hash - this is what we need to refer to in our reset command.
the commit message
So let's find the point we want to reset to:
    git log --oneline

We reset our repository back to the specific commit using git reset commithash (commithash being the first 7 characters of the commit hash we found in the log):

Example
    git reset 9a9add8
Now let's check the log again:

Example
    git log --oneline

Warning: Messing with the commit history of a repository can be dangerous. It is usually ok to make these kinds of changes to your own local repository. However, you should avoid making changes that rewrite history to remote repositories, especially if others are working with them.


Git Undo Reset
--------------
Even though the commits are no longer showing up in the log, it is not removed from Git.

If you know the commit hash you can reset to it:
    git reset e56ba1f
    git log --oneline

# Git Amend
Git commit --amend

commit --amend is used to modify the most recent commit.

It combines changes in the staging environment with the latest commit, and creates a new commit.

This new commit replaces the latest commit entirely.

Git Amend Commit Message
-------------------------

One of the simplest things you can do with --amend is to change a commit message.

Let's update the README.md and commit:
    git commit -m "Adding plines to readme"
    git log --oneline
Oh no! the commit message is full of spelling errors. Embarrassing. Let's amend that:
    git commit --amend -m "Added lines to README.md"
And re-check the log

Git Amend Files
----------------
Adding files with --amend works the same way as above. Just add them to the staging environment before committing.