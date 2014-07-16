Get Acquainted With Git[*](#this-just-covers-some-basic-git-commands-doesnt-cover-remote-repos-push-or-pull)
=======================

###Basic Commands
```git init```
Creates a new Git repository in the current directory. In addition, a directory named **.git** is added to the folder. This folder holds all the Git history and information for the repo. To get rid of the repo, just delete the .git folder

```git status```
Show me the current status of the repository. Shows
 
* **Untracked files** -- new files that have not be added to the staging or committed
* **Files that are tracked, have been changed but have not been staged**
* **Staged files** -- files that have been added but not commited

```git add .```
Adds all the files in the current directory to stagin.

```git add -A```
Adds all files in the current repo.

```git add -p```

```git add <path/to/file>```
Adds specified file to staging

```git commit -m "Add file to repo"```
Commit staged files to the repo

```git commit --amend -m "New Message"```
Changes the commit message for the last commit

```git commit -am "New Message"```
Let's you add **and** commit all tracked, modified files in one step.

```git log```
Show a log of all commits.

```git log --oneline```
Show a log of all commits, one line per commit

###Managing Files and Directories###
```git rm <path/to/file>``` Remove a file that's being tracked in the repo. If you haven't yet added the file to staging, this will produce an error. You may need to force the removal if the file is staged but not committed: ```git rm -f <path/to/file>```


```git rm -r <path/to/directory>``` Remove a directory's worth of files. Also removes the directory. Directories themselves aren't tracked in Git. You may need to force the remove if a file in the directory is staged but not committed: ```git rm -rf <path/to/directory>```

```git mv <path/to/file> <path/to/new-file-name>``` Move a file that's been committed to the repo.

```git mv <path/to/directory> <path/to/new-directory-name>``` Move a directory (and its files).

###Creating and Using Branches

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

```git checkout master```<br>
```git merge <name_of_branch>```
Return to master branch and merge changes from <name_of_branch> branch

###Getting Out of Changes
####File Fixes
```git reset HEAD <path/to/file>``` Unstage a file. (HEAD represents the current commit)

```git reset HEAD``` Unstage **all** staged files. 

```git checkout <path/to/file>``` To revert to the last committed version of a file but only if a) the file has been committed and b) is not currently in staging

```git checkout HEAD^ <path/to/file>``` Revert to version of file from prior commit (HEAD^ represents the prior commit). Careful: theis overwrites changes to files in your working branch.

```git checkout <sha-of-commit> <path/to/file>``` Revert to version of file from specific commit

####Revert Commits

```git reset --soft HEAD^``` Undo last commit of entire repo, but leave files staged.

```git reset --hard HEAD^``` Completely blow away last commit. Changes files to state of previous commit. 

```git reset --hard HEAD^^``` Completely blow away last two commits. Changes files to state of previous commit.

```git reset --hard HEAD^^^``` Completely blow away last three commits. Changes files to state prior to last third commit.

```git reset --hard <sha-of-commit>``` Returns files to state they were in after specificed commit

###Finding Differences Between Versions
```git diff``` View differences between current working files and staging area (or if files aren't staged compare working with last commit).

```git diff <path/to/file>``` View differences between current working file and staging area (or if file isn't staged compare working with last commit).


###A Simple Workflow
**Don't work on the master branch.**<br> Master branch should hold your working, production files. Don't mess with them. When you need to fix something, or add a new feature to your project, create a new working branch. Make changes to that branch, then merge them into the master branch when done. You can then deploy your master branch (push it up to a web server, for example)

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
8. Deploy master (push to web server for example).
9. Repeat steps 1-8 for your next feature/set of changes.

If things gets TOTALLY messed up in your working branch, you can just switch back to the master branch and delete the working branch:

1. ```git checkout master```
2. ```git branch -D <working_branch_name>```

Then just follow steps 1-7 again.


####*This just covers some basic Git commands. Doesn't cover remote repos, ```push``` or ```pull```
