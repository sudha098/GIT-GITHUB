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

Merge Conflict
--------------



