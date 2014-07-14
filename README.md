Get Acquainted With Git
=======================

###Basic Commands
```git init```
Creates a new Git repository in the current directory. In addition, a directory named **.git** is added to the folder. This folder holds all the Git history and information for the repo. To get rid of the repo, just delete the .git folder

```git status```
Show me the current status of the repository. Shows
 
* **Untracked files** -- new files that have not be added to the stage
* **Files that are tracked, have been changed but have not been staged**
* **Staged files** -- files that have been added but not commited

```git add .```
Adds all the files in the current directory to staging.

```git commit -m "Add file to repo"```
Commit staged files to the repo

```git log```
Show a log of all commits.

```git log --pretty=oneline```
Show a log of all commits, one line per commit

```git checkout -b <name_of_branch>```
Create a branch and check it out in one step

```git branch <name_of_branch>```
Create a branch, but stay in current branch.

```git checkout <name_of_branch>```
Check out an already created branch

```git branch```
See a list of all branchs, highlights the currently checked out branch

```git checkout master```
Checkout master branch

```git branch -d <name_of_branch>```
Remove branch

###Managing Files and Directories###
```git rm <file>``` Remove a file that's being tracked in the repo. If you haven't yet added the file to staging, this will produce an error. You may need to force the removal if the file is staged but not committed: ```git rm -f <file>```


```git rm -r <directory>``` Remove a directory's worth of files. Also removes the directory. Directories themselves aren't tracked in Git. You may need to force the remove if a file in the directory is staged but not committed: ```git rm -rf <directory>```

```git mv <file> <new-file-name>``` Move a file that's been committed to the repo.

###Getting Out of Changes
```git checkout <file>```
If you've made changes to a file that is 

* currently being tracked
* has NOT been added to the stage

```git reset HEAD <file>``` 
If you've made changes to a file that is

* currently being tracked 
* HAS been added to the stage




###A Simple Workflow
**Don't work on the master branch.**<br> Always create a new working branch. Make changes to that branch, then merge them into the master branch when done.

1. Make sure master is up-to-date.
Add and commit files, if there are any.
2. Create and checkout a new working branch:<br>
```git checkout -b <working_branch_name>```
3. Make changes to this branch. Make sure to add files and make commits along the way.
4. When done with branch:<br>
```git status```
Just to check and make sure that there are no outstanding changes that have yet to be committed. **If there are, add and commit files.**
5. Switch back to master<br>
```git checkout master```
6. Merge changes from working branch<br>
```git merge <working_branch_name>```
7. Remove branch<br>
```git -d branch <working_branch_name>```

If things gets TOTALLY messed up in your working branch, you can just switch back to the master branch and delete the working branch:

1. ```git checkout master```
2. ```git branch -d <working_branch_name>```

Then just follow steps 1-7 again.



